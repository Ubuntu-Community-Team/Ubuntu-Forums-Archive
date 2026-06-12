---
title: "Is this a hardware or software problem?"
date: 2016-01-26
forum: General Help
---

### Post by ross4 on 2016-01-26
I think my laptop (see system below) video card is failing. At power on, the screen shows many vertical lines of various colours. This continues through the bios screen, the boot menu and finally while Xubuntu is running. The only reason I even thought that it might be a software is that when I try to boot XP, it fails to boot, showing a screen "incriminating" the file nv4_mini.sys, which is the driver for the NVIDIA.

Is there any point in even trying to diagnose the problem further or should I just start right now to look for another machine?


Incidentally, at this moment I can still use Linux although the screen is rather hard to look at. Three cheers for 'buntu!


My system:
Toshiba Satellite P100 Laptop
Intel Core2 CPU
T5500 @ 1.66 GHz
1.67 GHz, 2.00 GB of RAM
Dual boot: XP & Xubuntu 14.04
HD: 63 GB for XP, 47 GB for Linux 
Video Card: NVIDIA GeForce Go 7600
Driver: nv4_mini.sys 01/01/2006

---

### Post by grahammechanical on 2016-01-26
If this is happening at the motherboard splash screen and when you have entered the motherboard BIOS set up utility and at the Grub menu then it is nothing to do with the video driver of any OS because the OS has not loaded. And the video driver loads as part of the loading of the OS.

Linux does not use the Windows video driver. So, if you are getting this effect on both Windows and Linux then it cannot be because Linux is using a corrupted Windows video driver. Linux will have its own video driver. It will either be the default open source video driver or the proprietary Nvidia driver. Either way it will not be the Windows driver that is being in used.

Regards.

---

### Post by ross4 on 2016-01-27
I more or less had that figured out but was wondering if a hardware fault on the graphics card, for example, could cause XP to prevent itself from booting while Xubuntu carries on? I know very little about drivers so I was speculating that the different drivers were reacting to the same initial problem in different ways. 
At any rate, my original question remains: Is there any point in trying to diagnose the problem (and what steps could I take) or is it time to look for a new machine (I've actually already started that)? 
Cheers.

---

### Post by mastablasta on 2016-01-28
it might be possible theoretically. 

in your case it's time for a newer PC. you can get good used ones (business grade) if you are short on money.

---

### Post by ross4 on 2016-01-30
Yes. In fact I've already picked up something. Thanks for the help.

---

