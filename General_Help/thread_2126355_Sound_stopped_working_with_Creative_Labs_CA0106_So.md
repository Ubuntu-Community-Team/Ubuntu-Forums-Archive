---
title: "Sound stopped working with Creative Labs CA0106 Soundblaster"
date: 2013-03-16
forum: General Help
---

### Post by malenkylizards on 2013-03-16
Hello all,

I installed this sound card several months ago.  At first it worked perfectly, but after maybe a couple of months there was no audio output (I lost track exactly when).  I now finally have enough time to devote to the problem, thanks to Spring Break.

I followed all relevant instructions in the Sound Troubleshooting Guide (by Lkjoel and Wildmanne39), to no effect.  The sound card and speakers all work fine when I use Windows XP.  One of the things I notice is that in the Sound Settings, the default device is the "Built-in Audio Analog Stereo", and while it recognizes the "CA0106 Soundblaster Analog Surround 5.1", it is always unselected when booting up.  It is the same in the hardware portion of the sound settings.

Here are some relevant outputs:
x@x:~$ lspci -nn | grep '\[04[80][13]\]'
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
04:06.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]

x@x:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have reinstalled ALSA.  I have edited /etc/asound.conf to set card 1 device 0 as the default.  Neither of these had any effect.  Not sure what else I can try at this point.  Thanks in advance for anything you can suggest!

---

### Post by malenkylizards on 2013-03-16
More information: I'm running 32-bit Ubuntu 12.04.  Please let me know if there's more information I can offer to make this problem easier to solve.

---

### Post by malenkylizards on 2013-03-16
If I had to speculate, I would say that whatever the problem is, the output of aplay -l hints to it.  First of all, there are 4 devices associated with the card, and secondly, I don't know what to expect but it seems to be a very generic description that more or less just shows the driver, ca0106.  Is there anything atypical about that output, that hints to the problem?

---

