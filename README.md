# Backup Daemon for Linux

## Overview
This is a backup daemon designed for Linux systems. It periodically creates backups of specified directories based on the configurations provided in `config.yaml`.

## Features
- Automatic backup creation based on specified frequency (minutely, hourly, daily, weekly, monthly).
- Supports custom source and backup directories.
- Logs backup activities using syslog.
- Graceful shutdown on termination signal.

## Prerequisites
- C++ compiler supporting C++17.
- POSIX-compliant operating system (tested on Linux).

## Installation
1. Clone the repository: `git clone https://github.com/your/repository.git`
2. Compile the code: `g++ -std=c++17 -o backup_daemon backup_daemon.cpp -lstdc++fs`
3. Ensure `config.yaml` file is present in the same directory as the compiled executable.

## Usage
1. Customize `config.yaml` with the desired source directory, backup directory, and backup frequency.
2. Execute the compiled binary: `./backup_daemon`

## Configuration (config.yaml)
```yaml
sourceDirectory: "/path/to/source/directory"
backupDirectory: "/path/to/backup/directory"
frequency: "daily" # Options: minutely, hourly, daily, weekly, monthly
```

## Signals
- SIGTERM: Initiates a graceful shutdown of the daemon.

## Logging
The daemon logs its activities using syslog. Log entries are categorized as follows:

- LOG_NOTICE: Daemon startup and shutdown messages.
- LOG_INFO: Backup creation success messages.
- LOG_ERR: Error messages, including failure to open configuration file or create backup directory, and unsupported frequency format.