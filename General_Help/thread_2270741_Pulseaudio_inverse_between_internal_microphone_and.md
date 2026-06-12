---
title: "Pulseaudio inverse between internal microphone and unplugged microphone"
date: 2015-03-25
forum: General Help
---

### Post by mehdi8 on 2015-03-25
[COLOR=#000000]Hello, [/COLOR]

[COLOR=#000000]I have seen my issue in some forum before but nobody was able to give a solution , i have Ubuntu 14.04LTS in ASUS X550L [/COLOR]

[COLOR=#000000]the issue is in the microphone, by default pulseaudio set in input device[/COLOR][B] INTERNAL MICROPHONE, but its not working 

if i change inpute device to [B]MICROPHONE UNPLUGGED, my mic work perfectly, but after restart or some time pulseaudio set back [B]INTERNAL MICROPHONE again , so i have to switch it manual every time or every restart 

i tried to change : [B]sudo gedit /etc/pulse/default.pa puting : 
> [I]### Make some devices default
#set-default-sink output
set-default-source 2 or set-default-source analog-input-microphone
[/I]

i tried also this commands but nothing 


> pacmd set-source-port 2 'analog-input-microphone'

anybody have idea, sure it will help many peoples 

thanks[/B][/B][/B][/B]

---

### Post by dino99 on 2015-03-25
also get some trouble with pulseaudio here on vivid: the 'output devices' is always wrongly set to 'headphones' instead of 'line out' when a session is opened. Also have seen some other users complaining. I need to use 'pulseaudio volume control' to set the good setting. (paman)

---

### Post by mehdi8 on 2015-03-25
yes, it seems that pulseaudio generate lot of issue on internal microphones, but nobody gives solutions, i tried all options but always the same pulseaudio set wrong microphone and we have to set the good one manually, this is  **pacmd list-sources** output: 


```
Welcome to PulseAudio! Use "help" for usage information.
>>> 3 source(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_03.0.hdmi-surround.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 1950
    volume: 0: 100% 1: 100% 2: 100% 3: 100% 4: 100% 5: 100%
            0: 0,00 dB 1: 0,00 dB 2: 0,00 dB 3: 0,00 dB 4: 0,00 dB 5: 0,00 dB
            balance 0,00
    base volume: 100%
                 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max rewind: 0 KiB
    sample spec: s16le 6ch 44100Hz
    channel map: front-left,front-right,rear-left,rear-right,front-center,lfe
                 Surround 5.1
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 123,36 ms
    monitor_of: 0
    card: 0 <alsa_card.pci-0000_00_03.0>
    module: 5
    properties:
        device.description = "Monitor of Built-in Audio Digital Surround 5.1 (HDMI)"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xf7a1c000 irq 67"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0a0c"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    index: 1
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 1950
    volume: 0:  58% 1:  58%
            0: -14,02 dB 1: -14,02 dB
            balance 0,00
    base volume: 100%
                 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 371,52 ms
    monitor_of: 1
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 6
    properties:
        device.description = "Monitor of Built-in Audio Analog Stereo"
        device.class = "monitor"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7a18000 irq 66"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9c20"
        device.product.name = "Lynx Point-LP HD Audio Controller"
        device.form_factor = "internal"
        device.string = "1"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
  * index: 2
    name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    base volume:   8%
                 -66,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 371,52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC233 Analog"
        alsa.id = "ALC233 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7a18000 irq 66"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9c20"
        device.product.name = "Lynx Point-LP HD Audio Controller"
        device.form_factor = "internal"
        device.string = "front:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC233"
        alsa.components = "HDA:10ec0233,104311af,00100003"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-input-microphone-internal: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-microphone: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
    active port: <analog-input-microphone-internal>
```

---

### Post by lunalui on 2015-10-06
I have this very same problem (on ubuntu 14.04): any news on this?
thank you

---

### Post by lunalui on 2015-10-09
Just in case someone else is interested, the solution proposed [here]("http://blog.tiger-workshop.com/ubuntu-rear-microphone-not-working-on-ad1988b-sound-chip/") as number 2 (although perhaps not best possible) worked for me. You also need to reduce the volume to almost silent base/unamplified.

---

### Post by Hesediel on 2015-12-25
i waas able to run hdajackretask s in the link above but i didn't had the aspected solution, but now i dont see in the settings the level for noone of the 2 mics

---

