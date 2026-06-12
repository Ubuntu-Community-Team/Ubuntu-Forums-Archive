---
title: "GRUB Error 21"
date: 2007-09-25
forum: General Help
---

### Post by brmchill on 2007-09-25
Hi All, I have a PC running windows xp on one hard drive and Ubuntu on a seperate hard drive and xp being the main drive and it is setup for dual boot. What has happened is Ubuntu hard drive has failed completly and if I try to boot xp it will just keep restarting and if i try to boot Ubumntu it will say that all these different files are missing. If I unplug the ubuntu hard drive it will then give me the error 21 message. Would you know if i install Ubuntu on a new hard drive and place it on the slave would that fix it or is there more to it. Thanks..

---

### Post by ddrichardson on 2007-09-25
Error 21 is not finding a drive specified in menu.lst. You could use a utility like Super Grub Disk to repair grub, fitting a new drive and reinstalling ubuntu should give you back that option but there is something else causing XP to reboot.

---

### Post by dondad on 2007-09-25
> **brmchill said:**
> Hi All, I have a PC running windows xp on one hard drive and Ubuntu on a seperate hard drive and xp being the main drive and it is setup for dual boot. What has happened is Ubuntu hard drive has failed completly and if I try to boot xp it will just keep restarting and if i try to boot Ubumntu it will say that all these different files are missing. If I unplug the ubuntu hard drive it will then give me the error 21 message. Would you know if i install Ubuntu on a new hard drive and place it on the slave would that fix it or is there more to it. Thanks..

You could use supergrub or something else, but if your XP install is still there and you are going to redo ubuntu, then I would use your xp install disk to fix the mbr, which will give you an xp boot, then reinstall ubuntu which will fix grub with the new install. 

When you boot the xp instal disk, you will have an option to repair an installation. Take that option, which will send you to a command line. Type FIXMBR and it will ask if you want to replace it, say yes and it will put you back to a standard windows boot.

The error is because only a little bit of grub is in the boot sector. The rest is on the disk that is no longer there, so it cannot continue.

---

