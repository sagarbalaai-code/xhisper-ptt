# xhisper-ptt

Push-to-talk speech-to-text for Linux with Groq Whisper API.

## How It Works

1. Press your hotkey → starts recording
2. Speak
3. Press hotkey again → transcribes and types at cursor

## Installation

```bash
# Build
make

# Install with setuid (one-time root)
sudo make install-setuid

# Add your Groq API key
echo 'GROQ_API_KEY=your_key_here' >> ~/.env
```

## Setup Hotkey

In your desktop environment's keyboard settings, add a custom shortcut:

- **Command:** `/usr/local/bin/xhisper`
- **Hotkey:** Choose something convenient (F12, CapsLock, etc.)

## Requirements

- Linux with PipeWire
- Groq API key (free at console.groq.com)
- wl-clipboard (Wayland) or xclip (X11) for non-ASCII characters

## Configuration

Create `~/.config/xhisper/xhisperrc`:

```
long-recording-threshold : 1000
transcription-prompt     : ""
non-ascii-initial-delay : 0.15
non-ascii-default-delay : 0.025
silence-threshold       : -50
silence-percentage      : 95
```

## Troubleshooting

**Permission denied on /dev/uinput:**
```bash
sudo make install-setuid
```

**Unicode characters not typing:**
```bash
sudo apt install wl-clipboard
```

**View logs:**
```bash
xhisper --log
```

## Uninstall

```bash
sudo rm /usr/local/bin/xhisper
sudo rm /usr/local/bin/xhispertool
sudo rm /usr/local/bin/xhispertoold
sudo pkill xhispertoold
rm -f /tmp/xhisper*
```
