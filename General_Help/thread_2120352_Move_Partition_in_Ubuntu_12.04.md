---
title: "Move Partition in Ubuntu 12.04"
date: 2013-02-26
forum: General Help
---

### Post by trong291990 on 2013-02-26
Hi, i installed ubuntu 12.04 in my laptop, my hdd : 80Gb
I use one partition NTFS(20Gb) to install windows xp, 15Gb install ubuntu.
Now, i want to delete windows xp, and add 20Gb to ubuntu partition.
Please help me.
Sorry by my English :)

---

### Post by Bucky Ball on 2013-02-26
*Thread moved to **General Help**.*

Welcome to the forums. Boot from the LiveCD, get to the desktop, launch Gparted and delete the Windows NTFS partition. You can then resize (expand) your Ubuntu partition into the free space you've created. You will then need to reinstall grub to boot into Ubuntu. Easiest way is probably Boot Repair:

[http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

You want the 'Reinstall Grub' option which is shown in the screenshot some way down that link.

---

