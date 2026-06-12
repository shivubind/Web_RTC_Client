# Web RTC Client

This folder contains all client-related files for Web RTC.

## Files

- `livekit_client.py` - Main client application
- `config-client.yml` - Client configuration file
- `env.client.example` - Environment variables template
- `requirements-client.txt` - Python dependencies

## Quick Start

### 1. Install Dependencies

```bash
pip install -r requirements-client.txt
```

### 2. Configure

```bash
# Copy environment template
cp env.client.example .env.client

# Edit config file
nano config-client.yml
```

Edit `config-client.yml`:
- Set `livekit.url` to your LiveKit server URL
- Set `livekit.api_key` and `livekit.api_secret`
- Set `livekit.room` to match the server room name

### 3. Run

```bash
# From the client/ directory
python livekit_client.py

# Or with custom config
python livekit_client.py --config config-client.yml

# Disablepython livekit_client.py --config config-client.yml video
python livekit_client.py --no-video
```

## Configuration

See `config-client.yml` for all available settings:
- LiveKit server connection
- Audio settings
- Video/camera settings
- Logging

## Command Line Options

```bash
python livekit_client.py [OPTIONS]

Options:
  --config FILE       Config file path (default: config-client.yml)
  --room NAME         Room name (overrides config)
  --url URL           LiveKit server URL (overrides config)
  --identity NAME     Client identity (overrides config)
  --no-video          Disable camera/video
  --camera INDEX      Camera device index
```

## Remote Connection

To connect to a remote server, set in `config-client.yml`:

```yaml
livekit:
  url: "wss://192.168.0.125:7880"  # Remote server
  api_key: "your-api-key"
  api_secret: "your-api-secret"
  room: "Web RTC-room"
```

## Troubleshooting

### No audio
- Check microphone permissions
- Verify audio device is working
- Test with: `python -c "import pyaudio; p = pyaudio.PyAudio(); print(p.get_default_input_device_info())"`

### No video
- Check camera permissions
- Try different camera index: `--camera 1`
- Disable video: `--no-video`

### Connection failed
- Verify LiveKit server URL is correct
- Check API keys match server configuration
- Ensure room name matches server
- Check firewall/network settings

# Web_RTC_Client
