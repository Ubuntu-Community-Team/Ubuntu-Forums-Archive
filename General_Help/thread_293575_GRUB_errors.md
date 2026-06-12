---
title: "GRUB errors"
date: 2006-11-05
forum: General Help
---

### Post by GolfGeek on 2006-11-05
I have a dual boot system with Win98 and Ubuntu. After a recent software installation, I had to reboot (while running windows) and forgot that my flah drive (USB) was still plugged in. Whe GRUB loaded, I got an error 13 which translated to a noncompatible device so I removed the flash drive and rebooted but now I get error 23 (drvice not found or not present) I have windows running on hd0 and ubuntu on hd1. Not sure how to correct this error

---

### Post by Spano on 2006-11-05
Re-install Grub?
Boot the Ubuntu live disk, get a terminal and do:
```
sudo grub
```
then
```
grub> root (hd1,0)
grub> setup (hd0)
```
then quit and reboot
grub> root (hd1,0) - points Grub to Grub files in Ubuntu install
setup (hd0) - re-installs Grub to MBR

---

### Post by GolfGeek on 2006-11-06
Spano
Thanks for the reply. I'll be heading over to the site where I have that machine later today but I'm sure this will work

---

### Post by Spano on 2006-11-06
Your welcome.  Let me leave you with this:
[http://www.justlinux.com/forum/showthread.php?t=144294](http://www.justlinux.com/forum/showthread.php?t=144294)
Several rescue scenarios using Grub floppy and live disk.
Adios

---

