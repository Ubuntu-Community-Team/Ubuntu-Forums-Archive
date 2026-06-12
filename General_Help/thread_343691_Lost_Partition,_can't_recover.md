---
title: "Lost Partition, can't recover?"
date: 2007-01-21
forum: General Help
---

### Post by Ralenger on 2007-01-21
Hello, I'm new to Linux, and have run into quite a problem (for me, at least).
Basically, I fell afoul of the MBR problems that I've since learned can occur on a dual-boot Ubuntu/XP system.  However, the partition Ubuntu is on has now vanished.  I installed Ubuntu on a slave drive, and it cannot mount the primary, nor does gparted recognise it, it's simply 'unallocated', TestDisk can't help either, although it at least acknowledges that it *was* a linux drive.

Is there any way to access the data on the drive, or have I lost it all?

---

### Post by Ralenger on 2007-01-21
So... I've lost it all, huh?

---

### Post by bodhi.zazen on 2007-01-21
Perhaps ...

You need to know the partition geometry (what was the partition table before). If you have not resized the unallocated space, partition it with cfdisk.

boot to the live CD, open a terminal

Enter:```
sudo cfdisk /dev/hdb
```

or /dev/sdb ....

Add a Linux partition using all of the unallocated space ....

Save and Exit cfdisk

Reboot (to hard drive) and [-o<

[http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html](http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html)

---

### Post by Ralenger on 2007-01-22
WOO, YES!

Thank you, I owe you one!

After following your suggestion (and tweaking the Grub boot list to include the drive), I seem to have a fully-restored system.  

Muchos Gracias.  :biggrin:

---

