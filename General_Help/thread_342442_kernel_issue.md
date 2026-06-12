---
title: "kernel issue"
date: 2007-01-20
forum: General Help
---

### Post by energiya on 2007-01-20
Hi,
I have some troubles booting any home-compiled kernel. I have tried with 2.6.17-10, 2.6.19, 2.6.19-2. I have the same problem with all of them. After rebooting, I get a **black screen (no cursor) and about 30 sec. of hdd reading, and then all dies, and have to use the power button**. I tried compiling about 10 times, with no modification to the standard config, with some changes, and havely customized, using menuconfig and xconfig.

Is it the **hardware**? (don't think so...) Is it **Ubuntu**? (I'm using Ubuntu Edgy) :confused: 

AMD Athlon XP 1700+
Gigabyte KT600 GA-7VT600 (K7 Triton)
Kingmax DDR400 128 MB
On-board sound (VIA AC'97)
Asus CD-ROM
WD 40GB JB
RIVA TNT2 M64 Pro 32MB

P.S.
I have succesfully compiled a few years ago on Red Hat and Mandrake, but was using another computer.

Thanks

---

### Post by energiya on 2007-01-24
oookk... I'm a true idiot... I have forgotten to uninstall the nVidia kernel, and said Y to another framebuffer...

ADVICE for all you kernel compilers... don't forget about the video drivers and framebuffer setting (the blank screen)

---

