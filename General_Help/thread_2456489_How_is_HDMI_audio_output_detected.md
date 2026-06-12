---
title: "How is HDMI audio output detected?"
date: 2021-01-12
forum: General Help
---

### Post by yaminb on 2021-01-12
I've been facing minor frustration with HDMI audio output.

I have 2 monitors (both with speakers) connected via HDMI including audio.
My left monitor is my main monitor and I'll generally always have it on.
My right monitor is just there when I need the space and it's sometimes on and sometimes off.

The problem is that the HDMI audio output names don't seem consistent in the naming. It results in a kind of trial and error each time I want to select the audio output.

They show up as:
HDMI / DisplayPort (TU106 High Definition Audio Controller)
HDMI / DisplayPort 2 (TU106 High Definition Audio Controller)

Yet, depending on the boot or when things come out of sleep, my left monitor audio is sometimes HDMI (1) and sometimes HDMI (2).
There's no consistency resulting in trial and error each time I want to select the audio out.

Is this expected? Is there a way to reliably configure this and maybe even give them better names for my own convenience?

---

### Post by grahammechanical on 2021-01-12
I think that you need to have a routine for shutdown or hibernation. Decide which monitor is to be on during the boot process or decide that both monitors should be on when booting or coming out of hibernation.

The boot process detects hardware and assigns it a label and does not use a rigid list. This allows us to upgrade certain items of hardware without breaking the OS.

Regards

---

### Post by yaminb on 2021-01-12
thanks graham.
Maybe I'm poking down the wrong hole, but I started poking around listing devices.
My thinking was there's probably some device id for the audio ouput. Then there's probably some configuration file, I can use that device id.

What's weird is that when I list the audio outputs, it only ever lists one for the HDMI output even with both monitors on. I should mention both HDMI outputs are hooked up to a single Nvidia graphics card.



```

 pactl list sinks
Sink #0
    State: SUSPENDED
    Name: alsa_output.pci-0000_05_00.1.hdmi-stereo-extra1
    Description: TU106 High Definition Audio Controller Digital Stereo (HDMI 2)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 7
    Mute: no
    Volume: front-left: 51967 /  79% / -6.05 dB,   front-right: 51967 /  79% / -6.05 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor Source: alsa_output.pci-0000_05_00.1.hdmi-stereo-extra1.monitor
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE DECIBEL_VOLUME LATENCY SET_FORMATS 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 1"
        alsa.id = "HDMI 1"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "7"
        alsa.card = "0"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xfc080000 irq 74"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:05:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:03.1/0000:05:00.1/sound/card0"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "10f9"
        device.product.name = "TU106 High Definition Audio Controller"
        device.string = "hdmi:0,1"
        device.buffering.buffer_size = "17664"
        device.buffering.fragment_size = "2944"
        device.access_mode = "mmap"
        device.profile.name = "hdmi-stereo-extra1"
        device.profile.description = "Digital Stereo (HDMI 2)"
        device.description = "TU106 High Definition Audio Controller Digital Stereo (HDMI 2)"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        hdmi-output-1: HDMI / DisplayPort 2 (type: Unknown, priority: 5800, availability group: Legacy 1, available)
    Active Port: hdmi-output-1
    Formats:
        pcm



```

I thought I'd see two entries, or possibly two ports. It's just weird. The problem is not too annoying, but I'm trying to use it as a learning process.

The only variable I do see is the Active Port. 
this seems to indicate which one it is pointing to:
Active Port: hdmi-output-1
Vs
Active Port: hdmi-output-0

---

### Post by HermanAB on 2021-01-12
These devices are detected the moment you plug them in/switch them on - they actually have a serial data channel on the HDMI port which allows the computer to interrogate the screen to see what resolutions it can handle.  You can see what happens with the *dmesg* command.

It used to be the udev system, but now I think it is done by systemd.  The issue is that the system cannot reliably distinguish between the two devices - you should be able to force it, but I cannot tell you how.

---

