---
title: "Grub rebooting problem"
date: 2007-08-15
forum: General Help
---

### Post by NTITech on 2007-08-15
I have both Windows Vista and Ubuntu Feisty installed on my system.  I use GRUB to boot my system.  I don't know why, but sometimes the GRUB menu wont appear.  Sometimes it just says "Stage 1.5" and then reboots.  The only way to fix it is to load up an Ubuntu live CD, open a terminal and type sudo grub, and use the root (hd0,2) and setup (hd0) commands.  That will fix GRUB, but not permanently, it'll work for a while, and then stop working and I have to fix it all over again.  Is there a permanent fix?  I need to use GRUB in the MBR, I cannot use the Vista bootloader (because I also have a 3rd OS installed =0 ).  Thanks in advance for your help.

---

### Post by chicoicho on 2007-08-15
Download this Boot Loader write  in cd and boot  [http://chicoicho.data.bg/bootloader.iso]("http://chicoicho.data.bg/bootloader.iso")

---

### Post by NTITech on 2007-08-16
> **chicoicho said:**
> Download this Boot Loader write  in cd and boot  [http://chicoicho.data.bg/bootloader.iso]("http://chicoicho.data.bg/bootloader.iso")

The server at store4.data.bg is taking too long to respond. :|

---

### Post by NTITech on 2007-08-16
*bump

---

### Post by chicoicho on 2007-08-16
Here link [http://ivkanum.hit.bg/images/bootloader.iso]("http://ivkanum.hit.bg/images/bootloader.iso")

---

### Post by NTITech on 2007-08-17
> **chicoicho said:**
> Here link [http://ivkanum.hit.bg/images/bootloader.iso]("http://ivkanum.hit.bg/images/bootloader.iso")

Is that just a Super GRUB Disc?  For some reason, when I try to use a Super GRUB Disc to repair GRUB, It reboots when it tries to write to the MBR...

---

