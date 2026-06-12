---
title: "Can not boot with USB device connected"
date: 2008-01-31
forum: General Help
---

### Post by TaintedTux on 2008-01-31
I have a machine that has two internal hard drives, one with Windows XP, and the other with Ubuntu Gutsy. I bought a WD 320gb My Book external HD today and connected it via USB. Anyways my problem is this, with the external hd, (or any USB device) connected, GRUB gives me error 21, and then will not load the boot menu, meaning that I can not boot my system with a USB device connected. The external HD automatically turns on with the computer so leaving it turned off is not really an option, and I really don't want to have to disconnect the usb cable everytime I need to reboot. I imagine this is an issue with a GRUB configuration or something, or possibly my machine trying to boot from the usb, but I believe that is disabled in my BIOS, so I think it is something with grub and problem an easy fix. Any ideas?

---

### Post by aJayRoo on 2008-01-31
I can't fix this but I do have the same problem with my WD 320GB MyBook on the same 2 disk setup. If you unmount the disk (from linux) before shutting down the machine, the disk should stay off during the next boot allowing you to turn it on manually after boot. Unfortunately the same is not true when using WinXP's safely remove device feature. The problem is very annoying, I have checked through the boot order in bios and can't see any reason why the error occurs.

---

