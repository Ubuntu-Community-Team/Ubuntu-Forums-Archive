---
title: "No Soundcards Found: 18.04 Dell XPS 13 9343"
date: 2018-05-15
forum: General Help
---

### Post by andrewxy on 2018-05-15
Hello all,

I'm currently dual booting Ubuntu 18.04 and Windows 10 which has caused audio headaches while using both OSs. About half of the time when booting into Ubuntu, the only sound sink would be a dummy output. The other half of the time the sound would seem to work fine. One time this week while trying to fix this problem for good, I tried some fixes others have posted online but I've only made the situation even worse (in Ubuntu at least). If anyone can help me identify my solution it would be greatly appreciated. Here is my current situation:

```

$  sudo aplay -laplay: device_list:270: no soundcards found...

$ pacmd list-sinks
1 sink(s) available.
  * index: 0
    name: <auto_null>
    driver: <module-null-sink.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 1000
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 344 KiB
    max rewind: 344 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
    module: 11
    properties:
        device.description = "Dummy Output"
        device.class = "abstract"
        device.icon_name = "audio-card"

$ find /lib/modules/`uname -r` | grep snd
[...large amount of text, I can post if it would be helpful...]

$ lspci -v | grep -A7 -i "audio"
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
    Subsystem: Dell Broadwell-U Audio Controller
    Flags: fast devsel, IRQ 255
    Memory at f741c000 (64-bit, non-prefetchable) [disabled] [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd_hda_intel


00:04.0 Signal processing controller: Intel Corporation Broadwell-U Processor Thermal Subsystem (rev 09)
    Subsystem: Dell Broadwell-U Processor Thermal Subsystem
--
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
    Subsystem: Dell Wildcat Point-LP High Definition Audio Controller
    Flags: bus master, fast devsel, latency 32, IRQ 48
    Memory at f7418000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3) (prog-if 00 [Normal decode])




```

---

### Post by andrewxy on 2018-05-16
Well, I couldn't figure it out so I decided to reinstall ubuntu. I'm back to the situation where changing between windows and ubuntu causes audio issues, but things could be worse.

---

