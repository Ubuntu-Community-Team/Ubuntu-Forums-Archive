---
title: "booting find 'wubi/boot/grub/menu.lst'"
date: 2007-08-30
forum: General Help
---

### Post by henky on 2007-08-30
hello, I've tried to install ubuntu via wubi, I have vista installed, now when I reboot, i get this message: booting find 'wubi/boot/grub/menu.lst'   
and it just hangs! i can wait 20 minutes but it still sais booting find 'wubi/boot/grub/menu.lst'

now what do I do??

thnx for any help:)

---

### Post by hh93 on 2007-08-30
> **henky said:**
> hello, I've tried to install ubuntu via wubi, I have vista installed, now when I reboot, i get this message: booting find 'wubi/boot/grub/menu.lst'   
and it just hangs! i can wait 20 minutes but it still sais booting find 'wubi/boot/grub/menu.lst'

now what do I do??

thnx for any help:)


Check this link out [http://ubuntuforums.org/archive/index.php/t-499834.html](http://ubuntuforums.org/archive/index.php/t-499834.html), may offer some help.

---

### Post by henky on 2007-08-30
> **hh93 said:**
> Check this link out [http://ubuntuforums.org/archive/index.php/t-499834.html](http://ubuntuforums.org/archive/index.php/t-499834.html), may offer some help.

thnx for your help, but I dont quite understand sorry,
by the hand of this trhead, could you tellme what to do?

---

### Post by hh93 on 2007-08-30
> **henky said:**
> thnx for your help, but I dont quite understand sorry,
by the hand of this trhead, could you tellme what to do?

i supposed you still could get to windows.
verify that 3 files, wubildr.mbr, wubildr, and boot.ini are present at c:\
also check if menu.lst is present within c:\wubi\boot\grub as well as in c:\wubi\boot\winboot and post their content.

---

### Post by henky on 2007-08-30
> **hh93 said:**
> i supposed you still could get to windows.
verify that 3 files, wubildr.mbr, wubildr, and boot.ini are present at c:\
also check if menu.lst is present within c:\wubi\boot\grub as well as in c:\wubi\boot\winboot and post their content.

I have windows vista;) vista does not use boot.ini:(

---

### Post by hh93 on 2007-08-30
> **henky said:**
> I have windows vista;) vista does not use boot.ini:(

sorry bout the mix-up, not familiar with vista.
in anycase, check these out [http://ubuntuforums.org/showthread.php?t=438858&highlight=vista+wubi](http://ubuntuforums.org/showthread.php?t=438858&highlight=vista+wubi)and [https://bugs.launchpad.net/wubi/+bug/113297](https://bugs.launchpad.net/wubi/+bug/113297), they might help

---

