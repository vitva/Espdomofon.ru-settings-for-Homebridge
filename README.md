# Espdomofon.ru-settings-for-Homebridge

**Board based on ESP8266. Allows you to remotely control a conventional coordinate intercom**

   Board setup [Espdomofon](https://github.com/Anonym-tsk/smart-domofon) drive using [Homebridge](https://github.com/homebridge/homebridge) and [MQTT](https://github.com/arachnetech/homebridge-mqttthing).

**Плата на основе ESP8266. Позволяет удаленно управлять обычным координатным домофоном**

Настройка платы [Espdomofon](https://github.com/Anonym-tsk/smart-domofon)
используя [Homebridge](https://github.com/homebridge/homebridge) и [MQTT](https://github.com/arachnetech/homebridge-mqttthing). 

### Example config.json

```
 {
            "accessory": "mqttthing",
            "type": "lockMechanism",
            "name": "Домофон",
            "url": "<url of MQTT server>",
            "topics": {
                "getLockCurrentState": "domofon/binary_sensor/domofon_button/state",
                "getLockTargetState": "domofon/switch/domofon_accept_call/state",
                "setLockTargetState": "domofon/switch/domofon_accept_call/command",
                "getOnline": "domofon/status"
            },
            "onlineValue": "online",
            "offlineValue": "offline",
            "lockValues": [
                "ON",
                "OFF",
                "Jammed",
                "Unknown"
            ]
        },
        {
            "accessory": "mqttthing",
            "type": "custom",
            "name": "Настройки домофона",
            "url": "<url of MQTT server>",
            "services": [
                {
                    "type": "switch",
                    "name": "Автооткр.",
                    "topics": {
                        "getOn": "domofon/switch/domofon_automatically_open/state",
                        "setOn": "domofon/switch/domofon_automatically_open/command",
                        "getOnline": "domofon/status"
                    },
                    "onValue": "ON",
                    "offValue": "OFF",
                    "onlineValue": "online",
                    "offlineValue": "offline"
                },
                {
                    "type": "switch",
                    "name": "Автооткр.1 раз",
                    "topics": {
                        "getOn": "domofon/switch/domofon_automatically_open_once/state",
                        "setOn": "domofon/switch/domofon_automatically_open_once/command",
                        "getOnline": "domofon/status"
                    },
                    "onValue": "ON",
                    "offValue": "OFF",
                    "onlineValue": "online",
                    "offlineValue": "offline"
                },
                {
                    "type": "switch",
                    "name": "Автосброс",
                    "topics": {
                        "getOn": "domofon/switch/domofon_automatically_reject/state",
                        "setOn": "domofon/switch/domofon_automatically_reject/command",
                        "getOnline": "domofon/status"
                    },
                    "onValue": "ON",
                    "offValue": "OFF",
                    "onlineValue": "online",
                    "offlineValue": "offline"
                },
                {
                    "type": "switch",
                    "name": "Сброс вызова",
                    "topics": {
                        "getOn": "domofon/switch/domofon_reject_call/state",
                        "setOn": "domofon/switch/domofon_reject_call/command",
                        "getOnline": "domofon/status"
                    },
                    "onValue": "ON",
                    "offValue": "OFF",
                    "onlineValue": "online",
                    "offlineValue": "offline"
                },
                {
                    "type": "switch",
                    "name": "Без звука",
                    "topics": {
                        "getOn": "domofon/switch/domofon_mute_sound/state ",
                        "setOn": "domofon/switch/domofon_mute_sound/command",
                        "getOnline": "domofon/status"
                    },
                    "onValue": "ON",
                    "offValue": "OFF",
                    "onlineValue": "online",
                    "offlineValue": "offline"
                },
                {
                    "type": "switch",
                    "name": "Без звука 1 раз",
                    "topics": {
                        "getOn": "domofon/switch/domofon_mute_sound_once/state",
                        "setOn": "domofon/switch/domofon_mute_sound_once/command",
                        "getOnline": "domofon/status"
                    },
                    "onValue": "ON",
                    "offValue": "OFF",
                    "onlineValue": "online",
                    "offlineValue": "offline"
                }
            ]
        }

```

If you want notifications from the camera in HomeKit during an incoming call, then you need to specify a topic in the plugin settings for your camera

Если хотите уведомления от камеры в HomeKit вовремя входящего звонка, то необходимо указать топик в настройках плагина к вашей камере

Plugin setup [Homebridge Camera FFmpeg](https://github.com/Sunoo/homebridge-camera-ffmpeg): 

```
"doorbellTopic": "domofon/binary_sensor/domofon_incoming_call/state",
                 "doorbellMessage": "ON"

```

