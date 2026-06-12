---
title: "Left and right audio playing out of the same speaker"
date: 2020-12-14
forum: General Help
---

### Post by robdo on 2020-12-14
I recently installed 20.10 on a new machine, I have a couple of computer speakers hooked up to the headphone jack but both channels are only playing through one of the speakers (they both work perfectly fine on other devices such as an iPhone so I've ruled out it being a problem with the speakers themselves). I've had a play around with alsamixer after reading that it can be a good place to start with these sorts of issues but everything seems to look fine.
[IMG]https://i.postimg.cc/3JLQ7JNG/Screenshot-from-2020-12-14-15-38-11.png[/IMG]
If anyone as any suggestions about what the problem might be or what else I should be looking at it would be greatly appreciated?

---

### Post by #&amp;thj^% on 2020-12-14
lets see if we can find the why, First will you check to see if volume for both channels have equal volume levels.
```
sudo apt install pavucontrol inxi
```
The code will install pulseaudio Volume Ctl along with inxi. (if needed)
Also show us this please:
```
 pacmd list-cards 
```

---

### Post by robdo on 2020-12-14
Thanks for your help :) I had a look at pavucontrol and both channels do have equal volume (initially their volume was linked), additionally when using the test feature in settings both the test for the left and right work but they both use the same speaker.

The output for `pacmd list-cards`:
```
1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_0e.0>
    driver: <module-alsa-card.c>
    owner module: 23
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xa1310000 irq 145"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:0e.0"
        sysfs.path = "/devices/pci0000:00/0000:00:0e.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "3198"
        device.product.name = "Celeron/Pentium Silver Processor High Definition Audio"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analogue Stereo Input (priority 65, available: no)
        output:analog-stereo: Analogue Stereo Output (priority 6500, available: unknown)
        output:analog-stereo+input:analog-stereo: Analogue Stereo Duplex (priority 6565, available: no)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_0e.0.analog-stereo/#1: Built-in Audio Analogue Stereo
    sources:
        alsa_output.pci-0000_00_0e.0.analog-stereo.monitor/#1: Monitor of Built-in Audio Analogue Stereo
    ports:
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "audio-headphones"

```

---

### Post by #&amp;thj^% on 2020-12-14
Interesting....
Mine shows:
```
1 card(s) available.
    index: 0
	name: <alsa_card.pci-0000_00_1f.3-platform-skl_hda_dsp_generic>
	driver: <module-alsa-card.c>
	owner module: 7
	properties:
		alsa.card = "0"
		alsa.card_name = "sof-hda-dsp"
		alsa.long_card_name = "LENOVO-20R10010US-ThinkPadX1Carbon7th"
		alsa.driver_name = "snd_soc_skl_hda_dsp"
		device.bus_path = "pci-0000:00:1f.3-platform-skl_hda_dsp_generic"
		sysfs.path = "/devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0"

```
That's just a short list of mine, your profiles is a bit confusing to me.

Example yours: "input:analog-stereo: Analogue Stereo Input (priority 65, **_available: no)_**"

Example Mine: "HiFi: Play HiFi quality Music (priority 8000, available: unknown)
		off: Off (priority 0, available: unknown)
	active profile: <HiFi>
"
Give me short time to talk to a developer, be back soon.

---

### Post by #&amp;thj^% on 2020-12-14
One more bit of info if you would please:
```
pacmd list-sinks 
```
Also I just wanted to verify that you also tried raising the Headphone volume in alsamixer while the headphones are **_unplugged_**.

---

### Post by robdo on 2020-12-14
Thank you so much for continuing to look at it, I really appreciate it!

When I unplug the speakers, 'Headphon' in alsamixer is toggled off and 'Speaker' is toggled on (I'm not sure what `Speaker` is, the machine has no internal or other speakers). With the speakers disconnected I can then turn up and un-mute 'Headphon', plugging the speakers back in will then toggle off `Speaker` and leave `Headphon` unmuted and at the volume I set. There is no difference in the audio play back, both channels still just play from one of the two speakers. To clarify as well, the volume and whether or not 'Speaker' is muted doesn't have an effect, just the volume of `Headphone`.

The output of `pacmd list-sinks` is this
```
1 sink(s) available.
  * index: 1
    name: <alsa_output.pci-0000_00_0e.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9039
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
    card: 0 <alsa_card.pci-0000_00_0e.0>
    module: 23
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC269VC Analog"
        alsa.id = "ALC269VC Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xa1310000 irq 145"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:0e.0"
        sysfs.path = "/devices/pci0000:00/0000:00:0e.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "3198"
        device.product.name = "Celeron/Pentium Silver Processor High Definition Audio"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "352800"
        device.buffering.fragment_size = "176400"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analogue Stereo"
        device.description = "Built-in Audio Analogue Stereo"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-headphones>
```

---

### Post by #&amp;thj^% on 2020-12-14
I can see no reason for this behaviour, I  have to ask if you ever used 20.04 LTS vs 20.10?
If so, did the same behaviour exist?
I'm still active on this problem of yours though. ;)
EDIT: Also I'm now curious is to how you wired your computer speakers to the Headset jack, even though they do work on other devices.

---

### Post by robdo on 2020-12-14
I haven't had 20.04 LTS on this machine no, it came with windows 10 installed but I didn't try the speakers on it before installing 20.10 :(. Auto-mute is enabled which might explain the `Headphon` toggling off when I disconnect the speakers. What I don't understand is the other `Speaker` listed in alsamixer as there's no other output available? I don't know if it's usual to have a control listed for internal speakers even if there aren't any?

---

### Post by robdo on 2020-12-14
If it's useful it's [this]("https://wiki.seeedstudio.com/ODYSSEY-X86J4105/") single board, maybe it being an sbc could be something to do with the `pacmd list-cards` output being unusual?

---

### Post by #&amp;thj^% on 2020-12-14
> **robdo said:**
>  I don't know if it's usual to have a control listed for internal speakers even if there aren't any?

Yep Normal. :)

> **robdo said:**
> I haven't had 20.04 LTS on this machine no, it came with windows 10 installed but I didn't try the speakers on it before installing 20.10 :(. as there's no other output available?
If windows is still an option to boot to, would you please try them on windows? (This will verify they work on your system )
Some hardware jacks and cords can be a bit finicky, and so far outside a first knee-jerk reaction from me, I really can't see anything wrong

---

### Post by #&amp;thj^% on 2020-12-14
> **robdo said:**
> If it's useful it's [this]("https://wiki.seeedstudio.com/ODYSSEY-X86J4105/") single board, maybe it being an sbc could be something to do with the `pacmd list-cards` output being unusual?

Silly me for not asking in the first place, :( "Microphone + headphone Combo Connector"
I'm not sure then on this,[s] the audio chip might not not be well supported here[/s]. Nope it's supported.
How well dose 20.10 run on this beast. :)
BTW some of those sbc's headphone jack meant single ear/phone.
Again i suspect the boards jack input needing a specific male jack input.

---

### Post by robdo on 2020-12-14
Thanks for the advice, it would make a lot of sense if that was the problem! I’m not with the machine right now but I’ll try running windows off a usb tomorrow.

It runs like a dream! I almost went with a lighter weight distro thinking that it would struggle but if anything it feels more responsive on Ubuntu than the 2015 MacBook Pro I use for work does on Mac OS :’)

---

### Post by #&amp;thj^% on 2020-12-14
:) Good Luck, and keep me posted.

---

### Post by robdo on 2020-12-17
I've not been able to test it on windows 10 yet, I'm trying to get a live USB install of windows 10 working to check and that's proving to be a pain, I'll post back if/when I do! However, I've picked up a cheap usb adapter for the speakers and using that doesn't have the same issue (as you would expect if it was just an issue with the board itself), which is good enough for me :) thanks again for all your help

---

### Post by CelticWarrior on 2020-12-17
> [COLOR=#000000]I'm trying to get a live USB install of windows 10 working to check and that's proving to be a pain[/COLOR]

There's no such thing.
If you already have a (professional, not "Home") Windows license and have it installed somewhere else, you can perhaps use the Windows To Go feature.
The suggested test implies running an installed Windows in the same hardware though.

---

