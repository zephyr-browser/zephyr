# 🚀 Quick Start Guide

Get Zephyr Browser up and running in minutes!

## Prerequisites

### Required
- **Rust 1.75+**: `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
- **Git**: For cloning the repository

### Platform-Specific

#### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install libgtk-4-dev libwebkit2gtk-4.1-dev build-essential
```

#### Linux (Fedora)
```bash
sudo dnf install gtk4-devel webkit2gtk4.1-devel
```

#### macOS
```bash
# Xcode Command Line Tools
xcode-select --install
```

#### Windows
- Install [Visual Studio Build Tools](https://visualstudio.microsoft.com/downloads/)
- WebView2 Runtime (usually pre-installed on Windows 11)

### Optional
- **Bun**: `curl -fsSL https://bun.sh/install | bash`

## Installation

### Option 1: From Source (Recommended)

```bash
# Clone the repository
git clone https://github.com/zephyr-browser/zephyr.git
cd zephyr

# Build release version
cargo build --release

# Run
./target/release/zephyr
```

### Option 2: Using Build Script

```bash
git clone https://github.com/zephyr-browser/zephyr.git
cd zephyr

# Check prerequisites
./build.sh check

# Build and install
./build.sh install
```

### Option 3: Cargo Install

```bash
cargo install zephyr-browser
zephyr
```

## First Run

When you first launch Zephyr:

1. **Welcome Screen**: You'll see a minimal welcome page
2. **Address Bar**: Click or press `Ctrl+L` to start browsing
3. **Quick Actions**: Try the protocol cards (IPFS, Gemini, etc.)

## Basic Usage

### Navigation
- **Enter URL**: Type in address bar, press Enter
- **Search**: Type search query, press Enter (uses DuckDuckGo)
- **Go Back**: `Ctrl+[` or click ← button
- **Go Forward**: `Ctrl+]` or click → button
- **Refresh**: `Ctrl+R` or click ↻ button

### Tabs
- **New Tab**: `Ctrl+T`
- **Close Tab**: `Ctrl+W`
- **Next Tab**: `Ctrl+Tab`
- **Previous Tab**: `Ctrl+Shift+Tab`

### Other
- **Zoom In**: `Ctrl++`
- **Zoom Out**: `Ctrl+-`
- **Reset Zoom**: `Ctrl+0`
- **Find**: `Ctrl+F`

## Configuration

Create `~/.config/zephyr/config.toml`:

```toml
[browser]
homepage = "https://duckduckgo.com"

[ui]
theme = "dark"  # or "light" or "auto"

[network]
enable_http3 = true

[protocols]
enabled = ["http", "https", "ipfs", "gemini"]
```

See `config.example.toml` for all options.

## Try These URLs

### Standard Web
```
https://example.com
https://news.ycombinator.com
https://github.com
```

### IPFS
```
ipfs://QmXoypizjW3WknFiJnKLwHCnL72vedxjQkDDP1mXWo6uco
```

### Gemini
```
gemini://gemini.circumlunar.space
gemini://medusae.space
```

## Troubleshooting

### Linux: "cannot find -lgtk-4"
```bash
sudo apt install libgtk-4-dev
```

### macOS: "ld: framework not found WebKit"
```bash
xcode-select --install
```

### Windows: WebView2 not found
Download from: https://developer.microsoft.com/en-us/microsoft-edge/webview2/

### Build fails with "linking failed"
```bash
# Clean and rebuild
cargo clean
cargo build --release
```

### Browser crashes on startup
```bash
# Check dependencies
ldd target/release/zephyr  # Linux
otool -L target/release/zephyr  # macOS

# Run with debug info
RUST_LOG=debug cargo run
```

## Performance Tips

1. **Use release build**: Debug builds are much slower
   ```bash
   cargo build --release
   ```

2. **Close unused tabs**: Each tab uses memory

3. **Clear cache**: If browsing feels slow
   ```bash
   rm -rf ~/.cache/zephyr
   ```

## Next Steps

- Read the [Architecture Guide](docs/ARCHITECTURE.md)
- Check [Performance Guide](docs/PERFORMANCE.md)
- See [Contributing Guidelines](CONTRIBUTING.md)
- Try different protocols (IPFS, Gemini)
- Customize your config file

## Getting Help

- **Issues**: https://github.com/zephyr-browser/zephyr/issues
- **Discussions**: https://github.com/zephyr-browser/zephyr/discussions
- **Documentation**: Check the `docs/` folder

## Update Zephyr

### From source
```bash
cd zephyr
git pull
cargo build --release
```

### From cargo
```bash
cargo install zephyr-browser --force
```

Happy browsing! 🌊
