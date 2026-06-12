---
title: "Yet another problem with ATI"
date: 2008-05-22
forum: General Help
---

### Post by navk2005 on 2008-05-22
Hello all, this is my first post here. 

In essence, I'm experiencing the same difficulties with Linux many others that I've read about are experiencing. Whenever some type of 3d effect or anything that requires 3d acceleration is present on screen, my computer freezes. 

At times, you can move the mouse without any response and at other times, you can't. At times, you can see the screen frozen as it is and at other times, the screen goes black. 

This has happened for me in both Gutsy and Hardy. When there is no 2d acceleration present, the freeze-up doesn't happen until a while after linux has been turned on. However, within 2-3 mins, my computer freezes with any 3d acceleration-requiring app or thing is present on screen.
Any way to fix this? Linux is my only option for now as my antivirus program accidentally deleted the actual rundll32.exe thinking it was a fake on Windows XP. 

My computer specs:
-Soyo motherboard with a Via chipset
-ATI Radeon 9800 Pro AGP
-AMD Athlon XP 3000+
-2 gb memory.
-ubuntu 8.04 hardy

my BIOS settings on AGP:
AGP speed: 8x
AGP aperture size: 128 Mb

btw, this has happened on windows XP as well. But that was a driver issue. The via chipset has some clashes with the ATI card series. I resolved that issue simply by setting AGP acceleration in bios to 8x and agp acceleration via the ati drivers to 0.

I'm a linux newbie so if anyone requires anything from logs or w/e, please be somewhat detailed. Thanks!!

---

### Post by 00arthuryu on 2008-05-22
that sounds like your graphic card is overheating, that is what happened to my X1950pro when that happened on both ubuntu and XP.

but can you put print the posts of
```

gedit /etc/X11/xorg.conf

```
and
```

glxinfo

```
and tell us how you installed the ati drivers :)
Regards
Arthy

---

