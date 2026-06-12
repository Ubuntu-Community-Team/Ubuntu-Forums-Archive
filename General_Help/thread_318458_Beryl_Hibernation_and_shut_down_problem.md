---
title: "Beryl Hibernation and shut down problem"
date: 2006-12-14
forum: General Help
---

### Post by ctukel on 2006-12-14
My system is as follows:
HP Pavilion zt3000
ATI Mobility Radeon 9200, 64 MB Video Card
1920*1200 screen resolution
I installed Beryl 0.1.3
Problem:

It is running great except hibernation and shut down.
I get black screen, and computer stalls there when I attempt to **log out** or **hibernate**. Then I have to keep pressing power button until it shut down.
I had to change modeline for 1920x1200 since it didn't work after installing fglrx drivers. 
How can I get shut down/restart buttons on shutdown dialog box?

Any help? Thank you.

Caglar

---

### Post by nmincone on 2006-12-15
This has more to do with the video card driver your using than anything else. Your buttons will return when the suitable drivers are detected that are compatible with those features.
There's a lot of different talk around the ATI camp as far as to which driver is best. AIGLX, FGLX or ATI proprietary drivers. From what I know, I believe the ATI drivers will better work with hibernation & suspension over the other drivers. Some feel the other drivers offer better performance over the ATI ones. Follow the wiki's & STF's for information on updating your graphic drivers.
NOTE: tweaking your drivers is not for the faint of heart, usually only resolved through lots of trial and error.
Backup your /etc/X11/xorg.conf (#sudo cp /etc/X11/xorg.conf xorg_orig.conf) file before changing anything! It will make it much easier to return to the GUI from the CLI if things go wrong.

---

### Post by teddydov on 2007-01-03
I am having a similer problem with a similer Computer (without Beryl) and wanted to know if the changes to the video card had solved the problem?? Thanks

---

