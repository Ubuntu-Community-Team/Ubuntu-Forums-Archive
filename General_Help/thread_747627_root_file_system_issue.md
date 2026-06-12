---
title: "root file system issue"
date: 2008-04-06
forum: General Help
---

### Post by fuseblower1123 on 2008-04-06
I installed ubuntu 7.10 and have used it for months, and then I put XP on a second partition, and now I don't have a root file system and therefore cannot boot either operating systems. 
How can I change the mount point of my Ubuntu system (/dev/sda1) to (/)?

---

### Post by kyphi on 2008-04-07
The usual procedure is to install XP first and then Ubuntu because Ubuntu writes a boot menu for both operating systems whereas XP will write one for itself and destroy the boot menu of any other operating system.

Hopefully the following procedure will recover Ubuntu.

Using a live Ubuntu CD In a terminal type ```
sudo grub
find /boot/grub/stage1
```
This will return a value such as (hdx,y) - take note of x and y.
type the following having substituted the values of x and y```
root (hdx,y)
```
type ```
setup (hd0)
``` - 0 is the numeral 0.
type ```
quit
```
then exit the terminal - press Ctrl+d
Shut down the live session and reboot.

---

