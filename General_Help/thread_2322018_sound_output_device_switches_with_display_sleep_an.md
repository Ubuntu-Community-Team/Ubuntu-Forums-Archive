---
title: "sound output device switches with display sleep and wake after 16.04 upgrade"
date: 2016-04-25
forum: General Help
---

### Post by sailingboyLLB on 2016-04-25
i upgraded from 15.10 to 16.04 and have started to have a fairly simple but annoying sound problem that didn't happen before.  for no apparent reason the sound output device gets changed to a different device.  i have to change it back whenever i stop getting sound output.  it seems to be happening roughly once per day or more, but i've never been present when the switch has happened.  i have working sound, leave the computer, come back and now the output device is changed.  i change it back and it works and so the cycle goes.

thanks for the help.

---

### Post by sailingboyLLB on 2016-04-26
a little additional information that might help.

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

pacmd list-sinks
1 sink(s) available.
  * index: 0
    name: <alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra1>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9950
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_1f.3>
    module: 6
    properties:
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
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xdf120000 irq 129"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a170"
        device.product.name = "Sunrise Point-H HD Audio"
        device.form_factor = "internal"
        device.string = "hdmi:0,1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo-extra1"
        device.profile.description = "Digital Stereo (HDMI 2)"
        device.description = "Built-in Audio Digital Stereo (HDMI 2)"
        alsa.mixer_name = "Realtek ALC887-VD"
        alsa.components = "HDA:10ec0887,1849d887,00100302 HDA:80862809,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
                device.product.name = "XVT553SV"
    active port: <hdmi-output-1>

```

the device it switches to is "Speakers *Built-in Audio*" which is a little odd since it's a desktop without built in speakers or anything plugged into the analog outs.

---

### Post by sailingboyLLB on 2016-05-12
[update]  it seems not to be random, but happens when the display goes to sleep.  any advice?

---

### Post by sailingboyLLB on 2016-05-30
bump

---

### Post by Vaclav_Dedik on 2016-06-04
I have the same problem. Whenever the display turns off, the sound doesn't work. It gets fixed as soon as I open the sound settings. I tried to set default sink, default profile, default source but nothing seems to be working. I even tried to disable my on board sound card in BIOS but that wouldn't fix it neither.

I just noticed it happens only when I lock the screen and let the display go to sleep. If I turn off the display with the off button, it doesn't happen. Curious.

---

### Post by Vaclav_Dedik on 2016-06-05
Can I somehow find out what happens behind the scenes (i.e. in the console) when I open the sound settings? It would tell me what command I have to run after unlocking the screen to fix it.

---

### Post by sailingboyLLB on 2016-06-09
yeah i tried all the same with no luck.  one thing i thought of but couldn't figure out how to do was changing the card profiles' priorities such that it was the highest and may switch when it becomes available.  all i was able to do in the end was a make a script to switch the profile when i pushed a button on my IR remote.

this is what i used, but obviously it will depend on your specific cards and profiles.
```
 pacmd set-card-profile 0 output:hdmi-stereo-extra1+input:analog-stereo
```

0 is the "card index" and the remainder is the actual profile.  pacmd list-cards will give you a list of profiles to select from, and it will show "active" for the current one.

---

### Post by Vaclav_Dedik on 2016-06-09
That doesn't work for me unfortunately. I have both the correct profile and the correct card activated, but the sound still doesn't work until I launch unity-control-center... Pretty odd. I tried to run unity-control-center with -v flag to see the debug output, but nothing relevant is shown. No idea what's going on.

---

### Post by Vaclav_Dedik on 2016-06-09
Huh, I tried to run just "unity-control-center -h" (yeah, that just prints help) and it fixes the problem, lol. So I just need to figure out how to hook up the command to some unlock event and I am golden.

---

### Post by Vaclav_Dedik on 2016-06-09
Here, maybe someone has the same problem:

```

dbus-monitor --session "type='signal',interface='com.ubuntu.Upstart0_6'" | \
(
  while true; do
    read X
    if echo $X | grep "desktop-unlock" &> /dev/null; then
      unity-control-center -h >> /dev/null;
    fi
  done
)

```
Just create a script with this content, "chmod +x" it and have it run on background. And voila, sound works.

---

