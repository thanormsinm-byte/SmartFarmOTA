# SmartFarmOTA

บอร์ดรุ่น ESP32-C3 Super Mini

PubSubClient

ArduinoJson

Preferences

Board Manager

ESP32 --> V 3.3.3
8266 Not support
OTA

Normal = Current <> New && New(ETag)
Force = Force = True && New(ETag) Build format : YYYYMMDDHHMM //2026011207 2026 Jan 12:07
Test Mode : ดูรูปประกอบ

┌────────────┐ │ BOOT │ └─────┬──────┘ │ v ┌──────────────┐ │ MCU_GUARD │ │ (ESP Check) │ └─────┬────────┘ │ ESP8266 ├──────────────► [BLINK BUILTIN LED FOREVER] │ v ┌──────────────────┐ │ INIT SYSTEM │ └─────┬────────────┘ │ v ┌──────────────────┐ │ CONNECT WIFI │ │ + READ RSSI │ └─────┬────────────┘ │ Fail ├──────────────► [RUN NORMAL APP] │ v ┌────────────────────────────┐ │ SHOW VERSION / ETAG LOG │ │ Current vs New │ └─────┬──────────────────────┘ │ v ┌────────────────────────────┐ │ IDLE / SLEEP │◄──────────────┐ │ (Waiting for Intent) │ │ └─────┬───────────────┬──────┘ │ │ │ │ │ │ │ v v │ ┌──────────────┐ ┌─────────────────┐ │ │ BTN LONG │ │ FORCE OTA │ │ │ PRESS 3s │ │ TRIGGER │ │ └─────┬────────┘ │ (JSON / Web) │ │ │ └─────┬───────────┘ │ │ │ │ v v │ ┌──────────────────┐ ┌──────────────────┐ │ │ NORMAL OTA CHECK │ │ FORCE OTA CHECK │ │ │ │ │ │ │ │ - WiFi │ │ - WiFi │ │ │ - RSSI │ │ - RSSI │ │ │ - Version │ │ (Ignore Version) │ │ │ - ETag │ │ (Ignore ETag) │ │ │ - force=false │ └─────┬────────────┘ │ └─────┬────────────┘ │ │ │ Fail │ │ ├──────────────► [EXIT OTA] ───────────┘ │ v ┌──────────────────┐ │ START OTA │ │ UPDATE │ └─────┬────────────┘ │ v ┌──────────────────┐ │ REBOOT │ └──────────────────┘
