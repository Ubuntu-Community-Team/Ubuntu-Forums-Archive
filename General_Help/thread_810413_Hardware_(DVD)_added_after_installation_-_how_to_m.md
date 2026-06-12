---
title: "Hardware (DVD) added after installation - how to make it work?"
date: 2008-05-28
forum: General Help
---

### Post by persistentstubborn on 2008-05-28
I have 8.04 upgraded from 7.10 running on PC.

There were CD/RW and CDROM in the PC and I replaced CDROM with a DVD (secondarey slave, bridged properly BIOS recognizes it).

I've run ./MAKEDEV, but it hasn't changed anything in /etc/fstab or /etc/mtab.

I've deleted (./MAKEDEV -d /dev/scd0; ./MAKEDEV -d /dev/scd1) both, rebooted and made them again (./MAKEDEV /dev/scd0; ./MAKEDEV /dev/scd1) but they are now again as 2 cdrom in /etc/fstab and I can't mount neither of them.

What should I do? I'm p*$$ed off by various udev, modprobe, pcimodules, lspci, dmesg and various other "help" that vasted my time with no results, since obviously I don't know how to read them.

This frustration is not healthy and is main disatdantage of linux.:mad:](*,)

---

### Post by pointone on 2008-05-28
Why would anything in fstab change? The mount-point /media/cdrom# means nothing--you can mount DVDs, USB images, or anything else for that matter on /media/cdrom#. 

What happens when you try to mount?

---

### Post by persistentstubborn on 2008-05-28
> **pointone said:**
> Why would anything in fstab change? The mount-point /media/cdrom# means nothing--you can mount DVDs, USB images, or anything else for that matter on /media/cdrom#. 

What happens when you try to mount?

Tnx (I did it already).

The problem was with jumpering drives, (I got out CD jumpered as slave, than put DVD jumpered Cable Select, CDRW that was inside was jumpered master but was in slave part of the cable). Obviously, nothing could have been mounted :D

Anyway, thanks, it was frustrating. I thought I'm trough a nightmare again, but eventually found what I did wrong.

Now it works excellent!

Right now I'm setting virtualbox for my son to play Gnjindonjz games upon his request and I'm happy.

8.04 rocks.

---

