---
title: "Intel nuc Sound card digital audio output problem"
date: 2021-12-13
forum: General Help
---

### Post by logman on 2021-12-13
[FONT=arial][SIZE=2]I have installed Ubuntu 21.10 on my Intel NUC8I7HVK. 
I can't figure out how to configure my SPDIF out to connect to my speaker system. I have the correct mini-toslink to standard cable and I can see the laser light coming from the PC, so it is not likely a hardware problem.

The NUC audio is [/SIZE][/FONT]Realtek ALC700[FONT=arial][SIZE=2].

Can anyone help me properly configure my audio to recognize my SPDIF digital output and support 5.1 Dolby surround?

Latest Ubuntu 21.10 freshly installed
Linux Kernel up to date: 5.13.0-22-generic[/SIZE][/FONT]

[URL="https://www.dropbox.com/s/tvdivkhfcx5g7mm/Kuvakaappaus%202021-12-13%2007-21-58.png?dl=0"]Ubuntu Audio Panel only hdmi output
[/URL][Also Windows 10 Screenshots ]("https://www.dropbox.com/s/myxdut9bjntw3xt/%C3%A4%C3%A4nikortti.PNG?dl=0")

```

0:1f.3 Audio device [0403]: Intel Corporation CM238 HD Audio Controller [8086:a171] (rev 31)
    Subsystem: Intel Corporation CM238 HD Audio Controller [8086:2073]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
--
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Polaris 22 HDMI Audio [1002:ab08]
    Subsystem: Intel Corporation Polaris 22 HDMI Audio [8086:2073]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

```
```

cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC700
Codec: Intel Kabylake HDMI

```
```

dmesg | egrep -i "(alsa|sound)"
[    5.806786] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input46
[    5.806832] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input47
[    5.806876] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input48
[    5.806920] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input49
[    5.806961] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input50
[    5.807002] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input51
[    6.688904] input: HDA Intel PCH Headphone Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input52
[    6.688977] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input53
[    6.689033] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input54
[    6.689085] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input55
[    6.689135] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input56
[    6.689187] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input57
[    6.689239] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input58


```
```

dmesg | egrep -i "alsa|audio|sound|snd"
[    0.132422] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    5.762395] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    5.762785] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[    5.762896] snd_hda_intel 0000:01:00.1: Force to non-snoop mode
[    5.805898] snd_hda_intel 0000:01:00.1: bound 0000:01:00.0 (ops amdgpu_dm_audio_component_bind_ops [amdgpu])
[    5.806786] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input46
[    5.806832] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input47
[    5.806876] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input48
[    5.806920] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input49
[    5.806961] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input50
[    5.807002] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input51
[    5.880164] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    5.924321] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC700: line_outs=1 (0x1b/0x0/0x0/0x0/0x0) type:line
[    5.924325] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.924327] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    5.924328] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    5.924329] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x1e/0x0
[    5.924329] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    5.924330] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x13
[    5.924331] snd_hda_codec_realtek hdaudioC0D0:      Headset Mic=0x19
[    5.924332] snd_hda_codec_realtek hdaudioC0D0:      Headphone Mic=0x1a
[    5.924333] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    6.688904] input: HDA Intel PCH Headphone Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input52
[    6.688977] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input53
[    6.689033] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input54
[    6.689085] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input55
[    6.689135] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input56
[    6.689187] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input57
[    6.689239] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input58


```
```

aplay -l
**** Luettelo PLAYBACK laitteista ****
kortti 0: PCH [HDA Intel PCH], laite 0: ALC700 Analog [ALC700 Analog]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 0: PCH [HDA Intel PCH], laite 3: HDMI 0 [HDMI 0]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 0: PCH [HDA Intel PCH], laite 7: HDMI 1 [HDMI 1]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 0: PCH [HDA Intel PCH], laite 8: HDMI 2 [HDMI 2]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 0: PCH [HDA Intel PCH], laite 9: HDMI 3 [HDMI 3]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 0: PCH [HDA Intel PCH], laite 10: HDMI 4 [HDMI 4]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 1: HDMI [HDA ATI HDMI], laite 3: HDMI 0 [HDMI 0]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 1: HDMI [HDA ATI HDMI], laite 7: HDMI 1 [HDMI 1]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 1: HDMI [HDA ATI HDMI], laite 8: HDMI 2 [HDMI 2]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 1: HDMI [HDA ATI HDMI], laite 9: HDMI 3 [HDMI 3]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 1: HDMI [HDA ATI HDMI], laite 10: HDMI 4 [HDMI 4]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 1: HDMI [HDA ATI HDMI], laite 11: HDMI 5 [HDMI 5]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0


```

```

pacmd list-cards
2 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_01_00.1>
    driver: <module-alsa-card.c>
    owner module: 23
    properties:
        alsa.card = "1"
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xdb560000 irq 169"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "ab08"
        device.product.name = "Polaris 22 HDMI Audio"
        device.string = "1"
        device.description = "Polaris 22 HDMI Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Ulostulo (priority 5900, available: no)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Ulostulo (priority 800, available: no)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Ulostulo (priority 800, available: no)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Ulostulo (priority 5700, available: no)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Ulostulo (priority 600, available: no)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Ulostulo (priority 600, available: no)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Ulostulo (priority 5700, available: no)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Ulostulo (priority 600, available: no)
        output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Ulostulo (priority 600, available: no)
        output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Ulostulo (priority 5700, available: no)
        output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Ulostulo (priority 600, available: no)
        output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Ulostulo (priority 600, available: no)
        output:hdmi-stereo-extra4: Digital Stereo (HDMI 5) Ulostulo (priority 5700, available: no)
        output:hdmi-surround-extra4: Digital Surround 5.1 (HDMI 5) Ulostulo (priority 600, available: no)
        output:hdmi-surround71-extra4: Digital Surround 7.1 (HDMI 5) Ulostulo (priority 600, available: no)
        output:hdmi-stereo-extra5: Digital Stereo (HDMI 6) Ulostulo (priority 38468, available: unknown)
        off: Poissa (priority 0, available: unknown)
    active profile: <output:hdmi-stereo-extra5>
    sinks:
        alsa_output.pci-0000_01_00.1.hdmi-stereo-extra5/#1: Polaris 22 HDMI Audio Digital Stereo (HDMI 6)
    sources:
        alsa_output.pci-0000_01_00.1.hdmi-stereo-extra5.monitor/#2: Monitor of Polaris 22 HDMI Audio Digital Stereo (HDMI 6)
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-4: HDMI / DisplayPort 5 (priority 5500, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-5: HDMI / DisplayPort 6 (priority 5400, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
                device.product.name = "ASUS MG279"
    index: 1
    name: <alsa_card.pci-0000_00_1f.3>
    driver: <module-alsa-card.c>
    owner module: 24
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0x2fff020000 irq 170"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a171"
        device.product.name = "CM238 HD Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Sisäinen äänentoisto"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analoginen stereo Syöte (priority 32833, available: unknown)
        output:analog-stereo: Analoginen stereo Ulostulo (priority 6500, available: no)
        output:analog-stereo+input:analog-stereo: Analoginen stereo, molemmat suunnat (priority 6565, available: unknown)
        output:hdmi-stereo: Digital Stereo (HDMI) Ulostulo (priority 5900, available: no)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Ulostulo + Analoginen stereo Syöte (priority 5965, available: unknown)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Ulostulo (priority 800, available: no)
        output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Ulostulo + Analoginen stereo Syöte (priority 865, available: unknown)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Ulostulo (priority 800, available: no)
        output:hdmi-surround71+input:analog-stereo: Digital Surround 7.1 (HDMI) Ulostulo + Analoginen stereo Syöte (priority 865, available: unknown)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Ulostulo (priority 5700, available: no)
        output:hdmi-stereo-extra1+input:analog-stereo: Digital Stereo (HDMI 2) Ulostulo + Analoginen stereo Syöte (priority 5765, available: unknown)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Ulostulo (priority 600, available: no)
        output:hdmi-surround-extra1+input:analog-stereo: Digital Surround 5.1 (HDMI 2) Ulostulo + Analoginen stereo Syöte (priority 665, available: unknown)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Ulostulo (priority 600, available: no)
        output:hdmi-surround71-extra1+input:analog-stereo: Digital Surround 7.1 (HDMI 2) Ulostulo + Analoginen stereo Syöte (priority 665, available: unknown)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Ulostulo (priority 5700, available: no)
        output:hdmi-stereo-extra2+input:analog-stereo: Digital Stereo (HDMI 3) Ulostulo + Analoginen stereo Syöte (priority 5765, available: unknown)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Ulostulo (priority 600, available: no)
        output:hdmi-surround-extra2+input:analog-stereo: Digital Surround 5.1 (HDMI 3) Ulostulo + Analoginen stereo Syöte (priority 665, available: unknown)
        output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Ulostulo (priority 600, available: no)
        output:hdmi-surround71-extra2+input:analog-stereo: Digital Surround 7.1 (HDMI 3) Ulostulo + Analoginen stereo Syöte (priority 665, available: unknown)
        output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Ulostulo (priority 5700, available: no)
        output:hdmi-stereo-extra3+input:analog-stereo: Digital Stereo (HDMI 4) Ulostulo + Analoginen stereo Syöte (priority 5765, available: unknown)
        output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Ulostulo (priority 600, available: no)
        output:hdmi-surround-extra3+input:analog-stereo: Digital Surround 5.1 (HDMI 4) Ulostulo + Analoginen stereo Syöte (priority 665, available: unknown)
        output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Ulostulo (priority 600, available: no)
        output:hdmi-surround71-extra3+input:analog-stereo: Digital Surround 7.1 (HDMI 4) Ulostulo + Analoginen stereo Syöte (priority 665, available: unknown)
        output:hdmi-stereo-extra4: Digital Stereo (HDMI 5) Ulostulo (priority 5700, available: no)
        output:hdmi-stereo-extra4+input:analog-stereo: Digital Stereo (HDMI 5) Ulostulo + Analoginen stereo Syöte (priority 5765, available: unknown)
        output:hdmi-surround-extra4: Digital Surround 5.1 (HDMI 5) Ulostulo (priority 600, available: no)
        output:hdmi-surround-extra4+input:analog-stereo: Digital Surround 5.1 (HDMI 5) Ulostulo + Analoginen stereo Syöte (priority 665, available: unknown)
        output:hdmi-surround71-extra4: Digital Surround 7.1 (HDMI 5) Ulostulo (priority 600, available: no)
        output:hdmi-surround71-extra4+input:analog-stereo: Digital Surround 7.1 (HDMI 5) Ulostulo + Analoginen stereo Syöte (priority 665, available: unknown)
        off: Poissa (priority 0, available: unknown)
    active profile: <input:analog-stereo>
    sources:
        alsa_input.pci-0000_00_1f.3.analog-stereo/#1: Sisäinen äänentoisto Analoginen stereo
    ports:
        analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-headphone-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-headset-mic: Headset Microphone (priority 8800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-output-lineout: Line Out (priority 9000, latency offset 0 usec, available: no)
            properties:
                
        analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-4: HDMI / DisplayPort 5 (priority 5500, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"

```
```

pacmd list-sinks
1 sink(s) available.
  * index: 1
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo-extra5>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9030
    volume: front-left: 0 /   0% / -inf dB,   front-right: 0 /   0% / -inf dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: yes
    current latency: 0,00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 2
    sample spec: s16le 2 kan. 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 1837,33 ms
    card: 0 <alsa_card.pci-0000_01_00.1>
    module: 23
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 5"
        alsa.id = "HDMI 5"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "11"
        alsa.card = "1"
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xdb560000 irq 169"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "ab08"
        device.product.name = "Polaris 22 HDMI Audio"
        device.string = "hdmi:1,5"
        device.buffering.buffer_size = "352768"
        device.buffering.fragment_size = "176384"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo-extra5"
        device.profile.description = "Digital Stereo (HDMI 6)"
        device.description = "Polaris 22 HDMI Audio Digital Stereo (HDMI 6)"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-5: HDMI / DisplayPort 6 (priority 5400, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
                device.product.name = "ASUS MG279"
    active port: <hdmi-output-5>


```

---

