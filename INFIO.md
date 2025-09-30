# XAMPP Installation Guide for Linux

## Overview
This guide provides step-by-step instructions for installing and configuring XAMPP (Apache, MySQL, PHP, and Perl) on Linux systems.

## Prerequisites
- Linux operating system (Ubuntu, Debian, Arch, Manjaro, etc.)
- Administrative (sudo) privileges
- Internet connection for downloading packages

## Installation Steps

### 1. Download XAMPP
Download the latest XAMPP installer from the official Apache Friends website or obtain it via USB drive.

### 2. Make the Installer Executable
Navigate to your Downloads directory and set executable permissions:

```bash
cd ~/Downloads
chmod +x xampp-linux-x64-*-installer.run
```

### 3. Run the Installation
Execute the installer with administrative privileges:

```bash
sudo ./xampp-linux-x64-*-installer.run
```

### 4. Resolve libcrypt.so.1 Dependency (If Required)

If you encounter a `libcrypt.so.1` missing library error, resolve it based on your distribution:

#### For Ubuntu/Debian:
```bash
sudo apt update
sudo apt install libxcrypt-compat
```

#### For Arch/Manjaro:
```bash
sudo pacman -Syu libxcrypt-compat
```

#### Alternative Solution (Quick Fix):
```bash
cd /usr/lib
sudo ln -s libcrypt.so.2 libcrypt.so.1
```

## Usage

### Starting XAMPP Services
```bash
sudo /opt/lampp/lampp start
```

### Verification
Open your web browser and navigate to:
```
http://localhost
```

### Managing XAMPP Services

#### Stop Services:
```bash
sudo /opt/lampp/lampp stop
```

#### Restart Services:
```bash
sudo /opt/lampp/lampp restart
```

#### Check Status:
```bash
sudo /opt/lampp/lampp status
```

## Default Configuration

- **Installation Directory**: `/opt/lampp/`
- **Web Root**: `/opt/lampp/htdocs/`
- **Apache Port**: 80
- **MySQL Port**: 3306
- **phpMyAdmin**: `http://localhost/phpmyadmin`

## Troubleshooting

### Common Issues

1. **Port Conflicts**: If Apache fails to start, check if port 80 is already in use
2. **Permission Issues**: Ensure you're running commands with `sudo`
3. **Firewall**: Configure firewall to allow HTTP traffic on port 80

### Useful Commands
```bash
# Check if Apache is running
sudo netstat -tlnp | grep :80

# View XAMPP logs
sudo tail -f /opt/lampp/logs/error_log
```

## Security Considerations

⚠️ **Important**: XAMPP is designed for development purposes. For production environments:
- Change default passwords
- Disable unnecessary services
- Configure proper firewall rules
- Enable SSL/TLS encryption

## Uninstallation

To remove XAMPP completely:
```bash
sudo /opt/lampp/uninstall
sudo rm -rf /opt/lampp
```

---

**Status**: ✅ XAMPP successfully installed and Apache server running
