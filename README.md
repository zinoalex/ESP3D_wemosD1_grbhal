# ESP3D 3.0

Firmware for ESP8266/ESP8285 and ESP32 (original, pico, S2, S3, C3, C6) used with 3D printer/Sand-Table and CNC.

> **This fork is configured for Wemos D1 Mini (ESP8266 4MB) as a WiFi bridge for grblHAL (BTT Octopus Pro v1.1).**

## Build

This fork uses **GitHub Actions** to compile the firmware automatically. WiFi credentials are injected at build time via **GitHub Secrets** and never stored in the repository.

### Setup

1. Fork this repository
2. Go to **Settings → Secrets and variables → Actions** and create two secrets:
   - `WIFI_SSID` — your WiFi network name
   - `WIFI_PASSWORD` — your WiFi password
3. Push any change to trigger the build
4. Download the compiled `.bin` from **Actions → build-ci → Artifacts**

### Flash

Flash the downloaded `.bin` using [ESPWebTool](https://esptool.spacehuhn.com/) directly from Chrome or Edge — no software installation required.

- Offset: `0x0`
- Erase flash before flashing (recommended)

### Configuration

The `configuration.h` was generated with the [ESP3D-Configurator](https://luc-github.github.io/) with the following settings:

- **Board:** Wemos D1 Mini (ESP8266, 4MB flash, DIO mode)
- **Target firmware:** grblHAL
- **Protocol:** RAW Serial
- **Features:** WiFi, HTTP server, Telnet, mDNS, SSDP, Captive Portal, Web Update, Notifications

WiFi credentials are provided via `myconfig.h`, generated at build time from GitHub Secrets and never committed to the repository.

---

To compile ESP3D manually, edit `configuration.h` according to your needs or generate it using the [ESP3D-Configurator](https://luc-github.github.io/).

Please refer to [esp3d.io](https://esp3d.io) for full documentation and installation instructions.

---

## Warning

**Disclaimer:** The software is provided 'as is,' without any warranty of any kind, expressed or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software. It is essential that you carefully read and understand this disclaimer before using this software and its components. If you do not agree with any part of this disclaimer, please refrain from using the software.

---

## SSDP Discovery

- **Windows:** Go to the Network page
- **OSX:** TBD
- **Linux:** Install `gupnp-tools` and run `gssdp-discover -i <devicename> --timeout=3`
- **Android:** [SSDP/UPnP Scanner](https://play.google.com/store/apps/details?id=com.vgc.ssdpscan)

---

## Sponsors

Support ESP3D Development — [Become a Sponsor](https://github.com/sponsors/luc-github)

---

## Chat

Please use Discord.

---

## Credits: embedded code / inspiration

- FTP server from Jean-Michel Gallego https://github.com/gallegojm/Arduino-Ftp-Server
- WebDav server from David Gauchard https://github.com/d-a-v/ESPWebDAV
- MKS support from https://github.com/makerbase-mks/MKS-WIFI
- Line support from https://github.com/TridentTD/TridentTD_LineNotify
- Pushover support from https://github.com/ArduinoHannover/Pushover
- Email support from https://github.com/CosmicBoris/ESP8266SMTP
- Telegram support from https://medium.com/@xabaras/sending-a-message-to-a-telegram-channel-the-easy-way-eb0a0b32968
- HomeAssistant support from https://developers.home-assistant.io/docs/api/rest/

## Credits: libraries

- Websockets from Markus Sattler https://github.com/Links2004/arduinoWebSockets
- BMx280MI from Gregor Christandl https://bitbucket.org/christandlg/bmx280mi
- DHT sensor from beegee_tokyo http://desire.giesecke.tk/index.php/2018/01/30/esp32-dht11/
- ESP32SSDP from luc-github https://github.com/luc-github/ESP32SSDP
- ESP8266-Arduino-Lua from François Dugast https://github.com/luc-github/ESP8266-Arduino-Lua
- ESP8266 and ESP32 Oled Driver for SSD1306 from Daniel Eichhorn, Fabrice Weinberg https://github.com/ThingPulse/esp8266-oled-ssd1306
- LittleFS_esp32 from lorol https://github.com/lorol/LITTLEFS
- lv_arduino from Pavel Brychta https://littlevgl.com
- SdFat from Bill Greiman https://github.com/greiman/SdFat
- TFT_eSPI from Bodmer https://github.com/Bodmer/TFT_eSPI
- ESP8266 core https://github.com/esp8266/Arduino
- ESP32 core https://github.com/espressif/arduino-esp32
