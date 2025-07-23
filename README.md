# Solana Mint Address Generator

[![Rust](https://img.shields.io/badge/Rust-1.70+-orange.svg)](https://www.rust-lang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-blue.svg)](https://github.com/ReactOnAuth/Rust-Minter)
[![Performance](https://img.shields.io/badge/Performance-1M%2B%20attempts%2Fs-green.svg)](https://github.com/ReactOnAuth/Rust-Minter)
[![Output](https://img.shields.io/badge/Output-JSON%20%7C%20TXT-purple.svg)](https://github.com/ReactOnAuth/Rust-Minter)

A high-performance Rust application that generates Solana mint addresses ending with specific suffixes for pump.fun and lets.bonk tokens. The generator runs on all CPU cores at maximum utilization and exports addresses to JSON or TXT files.

## Features

- 🚀 **High Performance**: Utilizes all CPU cores at 100% capacity
- 🎯 **Targeted Generation**: Generates addresses ending with "pump" and "bonk" (case sensitive)
- ⚡ **Optimized Detection**: Combined suffix detection for 50% faster generation when using "both" mode
- 💾 **File Export**: Saves addresses to JSON or TXT files with timestamps
- 🛠️ **Cross-Platform**: Works on Windows, Linux, and macOS
- 📊 **Real-time Monitoring**: Progress tracking and performance metrics with keys/second display
- 🔧 **Flexible Output**: Choose between JSON and TXT formats

## Prerequisites

- **Rust** (latest stable version)
- **Git**

## Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/Kvickar/rustminter.git
cd rustminter
```

### 2. Build and Run
```bash
# Build release version
cargo build --release

# Test with a single address (JSON format)
cargo run --release -- pump --count 1

# Generate 1000 pump addresses (TXT format)
cargo run --release -- pump --count 1000 --format txt
```

## Usage

### Command Line Options

```bash
cargo run --release -- [COMMAND] [OPTIONS]

Commands:
  pump    Generate pump.fun addresses (ending with "pump")
  bonk    Generate lets.bonk addresses (ending with "bonk")
  both    Generate both types of addresses

Options:
  -c, --count <COUNT>        Number of addresses to generate [default: 1]
  -f, --format <FORMAT>      Output format (json or txt) [default: json]
  -o, --output <OUTPUT>      Output filename (optional, auto-generated if not provided)
  -h, --help                 Print help
```

### Examples

```bash
# Generate 1000 pump addresses in JSON format
cargo run --release -- pump --count 1000

# Generate 500 bonk addresses in TXT format
cargo run --release -- bonk --count 500 --format txt

# Generate both types (250 each) with custom filename - OPTIMIZED!
cargo run --release -- both --count 250 --output my_addresses

# Generate addresses with specific filename
cargo run --release -- pump --count 100 --output pump_keys.json
```

### Windows Batch Scripts

```bash
# Interactive menu
run.bat

# Performance benchmark
benchmark.bat

# Continuous generation (PUMP only)
auto_start.bat

# Continuous generation (both types)
auto_both.bat

# Manage backup files
manage_backups.bat
```

## Output Formats

### JSON Format
```json
[
  {
    "pub_key": "ABC123...pump",
    "private_key": "5KJvsngHeMpm884wtkJNzQGaCErckhHJBGFsvd3VyK5qMZXj3hS",
    "suffix_type": "pump",
    "created_at": "2024-01-15T10:30:00Z"
  }
]
```

### TXT Format
```
# Solana Mint Addresses - Generated with suffix 'pump'
# Generated at: 2024-01-15T10:30:00Z
# Format: public_key,private_key,suffix_type

ABC123...pump,5KJvsngHeMpm884wtkJNzQGaCErckhHJBGFsvd3VyK5qMZXj3hS,pump
```

## Performance

### Expected Performance (addresses/second):
- **2-core CPU**: ~200K attempts/second
- **4-core CPU**: ~400K attempts/second
- **8-core CPU**: ~800K attempts/second
- **16-core CPU**: ~1.6M attempts/second
- **32-core CPU**: ~3.2M attempts/second

### Optimization Features:
- **Combined Detection**: When using `both` mode, the generator checks for both "pump" and "bonk" suffixes simultaneously, resulting in ~50% faster generation compared to sequential processing
- **Real-time Metrics**: Displays keys/second rate during generation for performance monitoring
- **Batch Processing**: Efficient batch-level timing for accurate performance measurements

### Optimization Tips:
1. **Use release builds** for maximum performance
2. **Run on dedicated hardware** for sustained performance
3. **Use SSD storage** for faster binary loading
4. **Close unnecessary applications** to free up CPU resources

## File Structure

```
rustminter/
├── src/
│   └── main.rs              # Main application logic
├── Cargo.toml               # Rust dependencies
├── run.bat                  # Interactive Windows menu
├── auto_start.bat           # Continuous PUMP generation
├── auto_both.bat            # Continuous both types
├── benchmark.bat            # Performance testing
├── manage_backups.bat       # Backup management
└── README.md               # This file
```

## Output Files

### Auto-generated Filenames
- `pump_addresses_20240115_103000.json`: PUMP addresses in JSON format
- `bonk_addresses_20240115_103000.txt`: BONK addresses in TXT format
- `my_addresses_pump.json`: Custom filename with suffix

### File Contents
- **JSON**: Structured data with metadata
- **TXT**: CSV format with header comments

## Troubleshooting

### Common Issues:

1. **Compilation Errors**
   ```bash
   rustup update
   cargo clean
   cargo build --release
   ```

2. **Low Performance**
   - Check CPU usage in Task Manager
   - Close unnecessary applications
   - Ensure you're using release builds

3. **File Permission Errors**
   - Check write permissions in output directory
   - Ensure sufficient disk space
   - Close any applications that might have the file open

### Performance Debugging:
```bash
# Check CPU cores
wmic cpu get NumberOfCores,NumberOfLogicalProcessors

# Monitor process
tasklist /FI "IMAGENAME eq solana-mint-generator.exe"

# Monitor real-time performance
# The application now displays keys/second during generation
```

## Security Considerations

### For Production Use:
1. **Secure file storage** for generated addresses
2. **Backup generated files** regularly
3. **Use encrypted storage** for sensitive data
4. **Consider rate limiting** for public deployments
5. **Use VPN** for remote server access

### Private Key Security:
- Private keys are stored in base58 format
- Keys are saved in plain text files
- Ensure proper file permissions and access controls
- Consider encrypting output files for additional security 