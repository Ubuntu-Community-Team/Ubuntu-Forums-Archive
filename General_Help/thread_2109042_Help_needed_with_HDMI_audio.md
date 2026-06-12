---
title: "Help needed with HDMI audio"
date: 2013-01-26
forum: General Help
---

### Post by Amblikai on 2013-01-26
Hi folks, for days now i've been trying to get sound through HDMI and nothing i've tried works. It's immensely frustrating! 
I'm running Xubuntu 12.10 on a zotac zbox nano AD12. I bought it to use as an HTPC running XBMC, but i can't get sound working in Xubuntu nevermind xbmc.

The system is fully up to date, and i have installed the fglrx drivers.
Some info:
Output from ```
aplay -l
```
```
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
aplay -L:
```
```
default
    Playback/recording through the PulseAudio sound server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=Generic_1
    HD-Audio Generic, ALC892 Analog
    Default Audio Device
front:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Front speakers
surround40:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Direct sample mixing device
dmix:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC892 Digital
    Direct sample snooping device
hw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC892 Digital
    Hardware device with all software conversions

```

The SPDIF output isn't muted in alsamixer and i have HDMI selected in pavucontrol.

output of:
```

speaker-test -c 2 -r 48000 -l 2 -D hw:0,3

speaker-test 1.0.25

Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.640120
 0 - Front Left
 1 - Front Right
Time per period = 5.971916

```

Please help if you can, i would very much appreciate any help given. Please ask if more information is needed.
Thanks in advance.

---

### Post by Merrattic on 2013-01-27
Cable? They can be very fussy. Test on another setup, or find a cable you know works.

Also, try powering down Pc and monitor/tv. Remove hdmi cable.Unplug all from the mains and leave for a while. Connect up the hdmi cable then connect the power to PC and monitor. Start up.

---

