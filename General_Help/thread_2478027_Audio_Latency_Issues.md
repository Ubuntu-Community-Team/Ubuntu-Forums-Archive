---
title: "Audio Latency Issues"
date: 2022-08-14
forum: General Help
---

### Post by graystripe on 2022-08-14
I can't find an answer to this anywhere.

I didn't have this problem on Ubuntu 20.04 LTS on my old computer. It only became an issue after installing Ubuntu on my new machine. Upgrading to 22.04.1 LTS did not fix it.

For some reason, my computer's audio sinks are put to sleep immediately after output stops. This means that the startup latency of about half a second applies **every time** there is **any** pause in audio output whatsoever. As a result, short audio cues such as pressing the left and right speaker buttons to test audio output in settings do not play at all because the startup latency is longer than the sound that plays. The small gap of silence between "front" and "left/right" when pressing those buttons puts the sink back into idle mode, reintroducing the startup latency, and resulting in neither word playing. Voice chat is a nightmare as well. At first I thought it was mic issues with the person I was speaking with, but I have since realized that it's just the output device going to sleep immediately after they stop speaking. "Yes" or "No" answers are borderline impossible to hear, notification tones rarely play unless they're long enough to catch the end of them, podcasts are completely ruined, you get the picture. It's horrible.

I've tried disabling Pulseaudio's sleep when idle module. That isn't the cause, so I turned it back on. In fact, using the command **pacmd list-sinks** immediately after pausing audio lists the state as idle with the suspend cause set as "(none)". After waiting several seconds and running the command again, I can see Pulseaudio's suspension kick in as the 'suspend cause' changes to "IDLE". So something else is killing the sink as soon as audio output stops, and I'm not sure how to tackle it. The GPU is an RTX 3080 and the drivers & OS packages are installed and up to date. Does anyone have any suggestions?

Here are the outputs of **pacmd list-sinks** immediately after pausing audio playback.
```

1 sink(s) available.
  * index: 1
    name: <alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: IDLE
    suspend cause: (none)
    priority: 9032
    volume: front-left: 30419 /  46% / -20.00 dB,   front-right: 30419 /  46% / -20.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 68.58 ms
    max request: 14 KiB
    max rewind: 14 KiB
    monitor source: 1
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 2
    configured latency: 75.00 ms; range is 0.50 .. 341.33 ms
    card: 1 <alsa_card.pci-0000_00_1f.3-platform-skl_hda_dsp_generic>
    module: 23
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = ""
        alsa.id = "HDA Analog (*)"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "sof-hda-dsp"
        alsa.long_card_name = "Micro_StarInternationalCo.Ltd.-GE76Raider11UH-REV1.0-MS_17K3"
        alsa.driver_name = "snd_soc_skl_hda_dsp"
        device.bus_path = "pci-0000:00:1f.3-platform-skl_hda_dsp_generic"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "43c8"
        device.product.name = "Tiger Lake-H HD Audio Controller"
        device.string = "_ucm0003.hw:sofhdadsp"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "16384"
        device.access_mode = "mmap+timer"
        device.profile.name = "HiFi: hw:sofhdadsp: sink"
        device.profile.description = "Speaker + Headphones"
        alsa.mixer_device = "_ucm0003.hw:sofhdadsp"
        device.description = "Tiger Lake-H HD Audio Controller Speaker + Headphones"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        [Out] Speaker: Speaker (priority 100, latency offset 0 usec, available: unknown)
            properties:
                
        [Out] Headphones: Headphones (priority 200, latency offset 0 usec, available: no)
            properties:
                
    active port: <[Out] Speaker>
```

And after waiting a few seconds and running it again:
```

1 sink(s) available.
  * index: 1
    name: <alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9032
    volume: front-left: 30419 /  46% / -20.00 dB,   front-right: 30419 /  46% / -20.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 2
    configured latency: 0.00 ms; range is 0.50 .. 341.33 ms
    card: 1 <alsa_card.pci-0000_00_1f.3-platform-skl_hda_dsp_generic>
    module: 23
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = ""
        alsa.id = "HDA Analog (*)"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "sof-hda-dsp"
        alsa.long_card_name = "Micro_StarInternationalCo.Ltd.-GE76Raider11UH-REV1.0-MS_17K3"
        alsa.driver_name = "snd_soc_skl_hda_dsp"
        device.bus_path = "pci-0000:00:1f.3-platform-skl_hda_dsp_generic"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "43c8"
        device.product.name = "Tiger Lake-H HD Audio Controller"
        device.string = "_ucm0003.hw:sofhdadsp"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "16384"
        device.access_mode = "mmap+timer"
        device.profile.name = "HiFi: hw:sofhdadsp: sink"
        device.profile.description = "Speaker + Headphones"
        alsa.mixer_device = "_ucm0003.hw:sofhdadsp"
        device.description = "Tiger Lake-H HD Audio Controller Speaker + Headphones"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        [Out] Speaker: Speaker (priority 100, latency offset 0 usec, available: unknown)
            properties:
                
        [Out] Headphones: Headphones (priority 200, latency offset 0 usec, available: no)
            properties:
                
    active port: <[Out] Speaker>

```

---

### Post by graystripe on 2022-09-25
This issue persists after replacing pulseaudio with pipewire. I had a feeling it wasn't pulse that was causing it because nothing I did to pulse's config changed anything. Does anyone have any idea where the issue lies in this case? ALSA?

---

### Post by graystripe on 2022-10-23
This issue remains present on Ubuntu 22.10 which doesn't use pulseaudio. If anyone has any idea what's causing my audio to be delayed by half a second every time it goes silent for any duration at all, it would be great to hear from you.

---

