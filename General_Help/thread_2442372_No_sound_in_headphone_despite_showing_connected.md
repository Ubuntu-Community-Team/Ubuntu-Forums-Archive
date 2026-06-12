---
title: "No sound in headphone despite showing connected"
date: 2020-05-02
forum: General Help
---

### Post by mugseller on 2020-05-02
Hi ubuntu noob here... I know this issue is very common and well answered everywhere but I've looked and tried numerous solutions on google and still cannot resolve it...

I have kubuntu 18.04 installed, 
in pavucontrol it shows my headphone is connected, and there is indication that sound is playing.
[ATTACH=CONFIG]285722[/ATTACH]
yet in my headphone theres either no sound or some very quiet noises
some other screenshots of pavucontrol

[ATTACH=CONFIG]285725[/ATTACH][ATTACH=CONFIG]285724[/ATTACH]

screenshot of alsamixer
[ATTACH=CONFIG]285723[/ATTACH]

toggle everything to see if audio comes out of headphone (by muting and unmuting), no luck.


I really want to know how to properly debug but just do not have enough  knowledge of audio devices to even know where to start looking... 
Since I had no idea I did not modify any configuration files when im trying solutions online 
greatly greatly appreciate any help or guidance!!


Diagnostic infos:

here's the output of running the cmd "pacmd list-sinks" 
> 
1 sink(s) available.                                                                                                                                                                          
  * index: 78                                                                                                                                                                                 
        name: <alsa_output.pci-0000_00_1f.3.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: RUNNING
        suspend cause: 
        priority: 9039
        volume: front-left: 35392 /  54% / -16.05 dB,   front-right: 35392 /  54% / -16.05 dB
                balance 0.00
        base volume: 65536 / 100% / 0.00 dB
        volume steps: 65537
        muted: no
        current latency: 39.65 ms
        max request: 7 KiB
        max rewind: 64 KiB
        monitor source: 80
        sample spec: s16le 2ch 48000Hz
        channel map: front-left,front-right
                     Stereo
        used by: 1
        linked by: 3
        configured latency: 40.00 ms; range is 0.50 .. 341.33 ms
        card: 1 <alsa_card.pci-0000_00_1f.3>
        module: 8
        properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "ALC700 Analog"
                alsa.id = "ALC700 Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA Intel PCH"
                alsa.long_card_name = "HDA Intel PCH at 0x2fff020000 irq 151"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1f.3"
                sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "a171"
                device.product.name = "CM238 HD Audio Controller"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "65536"
                device.buffering.fragment_size = "32768"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Built-in Audio Analog Stereo"
                alsa.mixer_name = "Realtek ALC700"
                alsa.components = "HDA:10ec0700,80862073,00100005 HDA:8086280b,80860101,00100000"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        ports:
                analog-output-lineout: Line Out (priority 9900, latency offset 0 usec, available: no)
                        properties:

                analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: yes)
                        properties:
                                device.icon_name = "audio-headphones"
        active port: <analog-output-headphones>




Additional system information:
duobooting with Windows 10, sound works fine in windows so the problem is not with the sound card.

---

### Post by mugseller on 2020-05-02
Somehow it worked again after I let my computer sleep and came back to it...

---

