# Pocket Scanner

A stripped-down fork of the Temporal Replay 26 badge firmware. Phase 1 ships
a hardware-exercise demo (joystick, buttons, tilt, OLED, NeoPixel matrix).
Phase 2 layers BLE / WiFi / IR scanning on top.

- **Spec:** `docs/superpowers/specs/2026-05-11-pocket-scanner-design.md`
- **Plan:** `docs/superpowers/plans/2026-05-11-pocket-scanner.md`
- **Upstream:** https://github.com/Architeuthis-Flux/Temporal-Replay-26-Badge (pinned to `0.2.4`)

## Build & flash

First-time setup:
```
cd upstream/ignition && ./setup.sh
```

Rebuild + flash:
```
cd upstream/firmware
pio run -e echo-dev -t upload --upload-port /dev/cu.usbmodem2101
```

## Push a MicroPython app update (fast loop)

After the firmware is flashed, app `.py` files can be pushed without reflashing.
See `upstream/docs/08-file-manager.md` for the exact command.

## Restore to factory v0.2.4

```
~/Library/Arduino15/packages/esp32/tools/esptool_py/5.2.0/esptool \
  --port /dev/cu.usbmodem2101 --baud 921600 \
  write-flash 0x0 ../backups/firmware-v0.2.4/factory_echo_16MB.bin
```
