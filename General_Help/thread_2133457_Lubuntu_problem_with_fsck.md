---
title: "Lubuntu problem with fsck"
date: 2013-04-08
forum: General Help
---

### Post by mringer on 2013-04-08
Lubuntu 12.04, installed off the live CD. I think that this is much better than the 
previous version (X-ub 8.04) (and my thanks to developers) but there are some 
problems. When it does a periodic fsck on startup, it says:

checking disk 1 of 1     

or maybe       1 of 2

but it does not say which partition it is checking (it used to say this with 8.04). 
Please is there any way to make it do so? Thank you.

---

### Post by rnerwein on 2013-04-08
hi
i ain't know, but give /etc/default/rcS  --> VERBOSE=yes a shot.
ciao

---

### Post by efflandt on 2013-04-08
In a terminal read: **man fstab**

Typically /etc/fstab entry for the root file system would end with 1, which means it would be done first (1 of 2 or whatever).
Other partitions that may need to be checked end with 2 in fstab.

One issue I have with Lubuntu on a tablet PC when it fscks is that Lubuntu and Ubuntu 12.04 share a common /home on 32 GB SD card (Win7 Pro is on its 32 GB SSD).  So after Lubuntu checks 1 of 2, it reboots, putting me into Windows (because I need to hold Windows button and power button to boot from SD). I end up having to wait for Windows to boot, then shut it down, then boot into Lubuntu to check my /home partition, which then just continues without rebooting again.

---

