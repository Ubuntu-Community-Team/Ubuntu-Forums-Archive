---
title: "Webcamera microphone not working on multiple school computers"
date: 2021-04-13
forum: General Help
---

### Post by hhkristofer on 2021-04-13
Dear Ubuntu community,

I am currently helping my father-in-law with his Ubuntu machines. He owns a private primary school and has recently decided to switch from Windows to Ubuntu. (YAY!)
With this pandemic situation, the school currently runs a hybrid between physical and Zoom-oriented education. Due to this, every classroom is now outfitted with webcams with built-in microphones so that the teachers can freely walk around and not be tied to the desk by a conventional microphone with a wire.

However, on some of the machines (not all), the microphone isn't working. The camera works fine, but Zoom doesn't detect any sound coming in. It is important to note that the microphones connected in the microphone jack on the front and back works fine. It is only the webcam's microphone that is connected through a USB that isn't working.

We would really appreciate some guidance as we are both fairly new to Ubuntu.

[B]OS: Ubuntu 20.04.02
[/B]
Please let me know if there are any terminal commands i should write to give you the information that you require.

---

### Post by Xian on 2021-04-13
Can you provide the output of the following command?

```
[COLOR=#242729][FONT=Consolas]pacmd list-sources[/FONT][/COLOR]
```

---

### Post by speartip on 2021-04-14
This may be as simple as zoom not picking up your default Mic. Check in your Zoom settings - Audio - Microphone, & check in the box that it's using the right microphone. Also make sure that the input volume slider is moved across, as sometimes it can be muted by default.

---

### Post by hhkristofer on 2021-04-14
> **Xian said:**
> Can you provide the output of the following command?

```
[COLOR=#242729][FONT=Consolas]pacmd list-sources[/FONT][/COLOR]
```

```
3 source(s) available.
  * index: 0
    name: <alsa_input.usb-WCM_USB_WEB_CAM-02.multichannel-input>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9040
    volume: mono: 51401 /  78% / -6,33 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max rewind: 0 KiB
    sample spec: s16le 1ch 16000Hz
    channel map: mono
                 Mono
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 2000,00 ms
    card: 0 <alsa_card.usb-WCM_USB_WEB_CAM-02>
    module: 7
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "WEB CAM"
        alsa.long_card_name = "WCM_USB WEB CAM at usb-0000:00:12.2-3, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:12.2-usb-0:3:1.2"
        sysfs.path = "/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.2/sound/card1"
        udev.id = "usb-WCM_USB_WEB_CAM-02"
        device.bus = "usb"
        device.vendor.id = "1c3f"
        device.vendor.name = "WCM_USB"
        device.product.id = "2002"
        device.product.name = "WEB CAM"
        device.serial = "WCM_USB_WEB_CAM"
        device.form_factor = "webcam"
        device.string = "hw:1"
        device.buffering.buffer_size = "64000"
        device.buffering.fragment_size = "32000"
        device.access_mode = "mmap+timer"
        device.profile.name = "multichannel-input"
        device.profile.description = "Multicanal"
        device.description = "WEB CAM Multicanal"
        module-udev-detect.discovered = "1"
        device.icon_name = "camera-web-usb"
    ports:
        multichannel-input: Entrada multicanal (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
    active port: <multichannel-input>
    index: 1
    name: <alsa_output.pci-0000_00_14.2.analog-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 1030
    volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Estéreo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 1999,82 ms
    monitor_of: 0
    card: 1 <alsa_card.pci-0000_00_14.2>
    module: 8
    properties:
        device.description = "Monitor of Áudio interno Estéreo analógico"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HD-Audio Generic"
        alsa.long_card_name = "HD-Audio Generic at 0xfeb40000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1022"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD]"
        device.product.id = "780d"
        device.product.name = "FCH Azalia Controller"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    index: 2
    name: <alsa_input.pci-0000_00_14.2.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9039
    volume: front-left: 30420 /  46% / -20,00 dB,   front-right: 30420 /  46% / -20,00 dB
            balance 0,00
    base volume: 5841 /   9% / -63,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Estéreo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 1999,82 ms
    card: 1 <alsa_card.pci-0000_00_14.2>
    module: 8
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC662 rev1 Analog"
        alsa.id = "ALC662 rev1 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HD-Audio Generic"
        alsa.long_card_name = "HD-Audio Generic at 0xfeb40000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1022"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD]"
        device.product.id = "780d"
        device.product.name = "FCH Azalia Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "352768"
        device.buffering.fragment_size = "176384"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Estéreo analógico"
        device.description = "Áudio interno Estéreo analógico"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-input-front-mic: Microfone frontal (priority 8500, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-rear-mic: Microfone traseiro (priority 8200, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-linein: Entrada de linha (priority 8100, latency offset 0 usec, available: no)
            properties:
                
    active port: <analog-input-front-mic>
```

---

### Post by hhkristofer on 2021-04-14
> [COLOR=#000000]This may be as simple as zoom not picking up your default Mic. Check in your Zoom settings - Audio - Microphone, & check in the box that it's using the right microphone. Also make sure that the input volume slider is moved across, as sometimes it can be muted by default.[/COLOR]

I tried this, but it's not it. I have tried both options and played around with the sliders, but still nothing.

[https://ibb.co/Mn9C1Jy](https://ibb.co/Mn9C1Jy)

---

### Post by grahammechanical on 2021-04-14
I am also using Ubuntu 20.04.2 and I have zoom-client installed as a snap packaged app. The snap package brings in a later version of zoom-client than the one available on the zoom web site. And it gets updated regularly.

Every time I use zoom-client to join a meeting I cannot hear the host or any participants until I open System Settings>Sound and adjust the Zoom voice engine output from half way to full. I have to do this every time as half way is the default.

System Settings>Sound will offer some settings for zoom-client but only after zoom-client has joined a meeting. I would also check that the volume output setting of the computer is not over-riding the zoom-client output and so limiting the volume. The speakers themselves may have physical volume controls.

Looking at this from a different direction. Zoom-client>Participants will show which microphones are muted. And when a microphone is unmuted the dialog will show a progress bar giving the microphone volume level as sound is received in the microphone. It is an indication that the microphone is working. I am assuming that if the operating system does not recognise the microphone then zoom-client>participants will not show that participant as having a microphone - muted or not. I do not know about this.

You may already know these things and have checked them but at the moment we do not know if this is a problem with zoom-client or with Ubuntu recognising the hardware. I do not have a web-cam so I do not know where in System Settings I would go to check if it is detected. There is the assumption that the web-cam is detected but not the microphone. For microphones it is system Settings>Sound. As these are USB devices you may need to make an adjustment in the UEFI/BIOS settings utility. I am just guessing.

Regards

---

### Post by ActionParsnip on 2021-04-14
If you install and use pavucontrol does it help?

---

### Post by Xian on 2021-04-14
[COLOR=#242729][FONT=Consolas]The '*' next to your [/FONT][/COLOR][COLOR=#000000][FONT=&amp] index: 0 source indicates this is the default.[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]
This may be a suspend on idle issue.

 Edit your [/FONT][/COLOR]/etc/pulse/default.pa file and comment out the line:[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][FONT=Consolas]```
load-module module-suspend-on-idle
```[/FONT][FONT=Consolas]
Save changes to file.

Now restart pulseaudio[/FONT][COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]```
[FONT=Consolas]pulseaudio -k[/FONT]
```

Any change?

---

### Post by hhkristofer on 2021-04-15
Thanks, i tried this:

#load-module module-suspend-on-idle

Saved it and restarted pulseaudio, but still nothing. There is still no audio-bar under "Webcam" in pulseaudio.

When launching [COLOR=#535A60][FONT=Arial]pacmd list-sources, [/FONT][/COLOR]again, it now says this: 
```
[FONT=Consolas]

   name: <alsa_input.usb-WCM_USB_WEB_CAM-02.multichannel-input>[/FONT] 
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: IDLE
    suspend cause: (none)
```

This might be progress, it went from SUSPENDED to IDLE when not in use

---

