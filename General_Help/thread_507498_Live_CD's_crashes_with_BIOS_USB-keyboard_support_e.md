---
title: "Live CD's crashes with BIOS USB-keyboard support enabled"
date: 2007-07-23
forum: General Help
---

### Post by oz2kso on 2007-07-23
The Live CD's of both 
Ubuntu 7.04
Xubuntu 7.04
Zenwalk 4.6.1
crashes and reboots the PC while loading the Linux kernel (just after the first selection menu after booting from the CD)
I found that it was the BIOS USB-keyboard support, which coursed the problem! Disabling it made the CD boot, but then I have to go with the first choose in the menu... 

My BIOS is from 1999 and it works fine with a USB keyboard, but in 2007 GRUP (and other boot managers) are completely unaware of any kind of USB keyboard!?! Why???
Then the BIOS are kind enough to have a feature to workaround that floor, but that apparently make problems some ware else...
(Btw. it works fine with Damn Small Linux...?)

Does anyone have a comment about this issue, or shut I just live with it? I can't be the only one with this problem...

Thanks
Kenneth

---

### Post by benx009 on 2007-07-23
I guess the best thing you can do for now is just live w/ it.  I had a problem w/ one of my USB devices during a Feisty installation once.  Ubuntu would not install on my hard drive w/ the device (a flash drive) plugged in.  Of course, your problem is a lot more severe than mine ever was.  I know Ubuntu has problems detecting certain USB keyboards, but I'm sure later releases will attempt to fix this issure.

---

