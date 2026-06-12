---
title: "USB soundcard not working"
date: 2016-11-19
forum: General Help
---

### Post by jeff162 on 2016-11-19
Hi, I'm running Ubuntu-Mate 16.04 with the kxstudio repos.

I have a Steinberg CL1 but I'm not getting any audio from it. The light indicating it's working is off. It worked fine out of the box in 14.04. It's class-compliant. I'm trying to get it working but all the info out there is years out of date and the fixes I've tried here haven't worked out: [https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)    

I also set it as my default device under the sound preferences. I also did the unplugging and plugging back in thing.

Here is my kernel:
```
4.4.0-47-lowlatency


```

The output of aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Loopback [Loopback], device 0: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Loopback [Loopback], device 1: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: MID [HDA Intel MID], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: MID [HDA Intel MID], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: CI1 [Steinberg CI1], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```


The output of lsusb, I'm assuming its showing under Yamaha Corp, It uses  a yamaha chipset and I think it was listed that way previously:
```
Bus 002 Device 007: ID 1a86:752d QinHeng Electronics CH345 MIDI adapter
Bus 002 Device 006: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 005: ID 2467:2002  
Bus 002 Device 008: ID 0499:1501 Yamaha Corp. 
Bus 002 Device 003: ID 056a:0015 Wacom Co., Ltd Graphire 4 4x5
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]
Bus 001 Device 003: ID 09e8:0074 AKAI  Professional M.I. Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

Any help is certainly appreciated.

---

