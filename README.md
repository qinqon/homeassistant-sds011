# homeassistant-sds011
 Home-Assistant Custom Component for SDS011 Particulate Matter Sensor, with support for turning off sensor between measurements for longer laser life.

## Installation

Place the `sds011` directory in your `config/custom_components` directory so you end up with:
```
config/custom_components/sds011/
├── __init__.py
├── manifest.json
└── sensor.py
```

The `py-sds011` dependency will be installed automatically by Home Assistant via `manifest.json`.

## Configuration

Add the following to `configuration.yaml`:
```yaml
sensor:
 - platform: sds011
   serial_device: /dev/ttyUSB0  # required
   name: outside  # optional
   measure_interval: 150  # optional, seconds between measurements (default: 60)
   warmup_delay: 25  # optional, seconds to warm up sensor (default: 15)
   number_of_measurements: 5  # optional, samples to average (default: 5)
```

## Sensors

The component creates two sensor entities:
- **PM2.5** - Fine particulate matter (µg/m³)
- **PM10** - Coarse particulate matter (µg/m³)

Both sensors include proper device classes (`pm25` / `pm10`) and state class (`measurement`) for long-term statistics support in Home Assistant.
