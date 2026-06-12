---
title: "USB Soundcard --&gt; grayed out"
date: 2016-11-20
forum: General Help
---

### Post by elinu on 2016-11-20
Hi to all !

I installed c - media usb sound card and it was detected and working ok.
After that i try to set this card as first sound card and i installed one oss package. 
I reboot the system and now i can see all the sound cards but just one is active and others are greyed out.
The active one is onboard sound card.

I reinstalled whole alsa, deleted oss packages (with synaptic) and the situation is the same.
Funny part is that if i run lsusb i can see the usb card but when i run alsa -l i get just the onboard version.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
------------------------------------------------------------------------------
cat /proc/asound/cards
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeabc000 irq 44

------------------------------------------------------------------------------
       HD-Audio Generic at 0xfeabc000 irq 44
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0d8c:013c C-Media Electronics, Inc. 
Bus 003 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse

ALSA output:
[http://www.alsa-project.org/db/?f=e0e5e37e54fde8b41eb3ece81c1db7ed119441c2](http://www.alsa-project.org/db/?f=e0e5e37e54fde8b41eb3ece81c1db7ed119441c2)

Well, any info is more then welcome !
Thnx in advance !

---

### Post by elinu on 2016-11-22
Bump.

---

### Post by Yellow Pasque on 2016-11-22
```
[   15.478518] snd_usb_audio: `' invalid for parameter `index'
```

You typo'd when you added this line:
```
snd-usb-audio: index= 0
```
Should be index=0 (no space between '=' and 0)

---

