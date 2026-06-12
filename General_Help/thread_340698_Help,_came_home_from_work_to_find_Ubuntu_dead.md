---
title: "Help, came home from work to find Ubuntu dead"
date: 2007-01-17
forum: General Help
---

### Post by Tutu 1234 on 2007-01-17
Came home from work and my flatmate was logged into his account, so I logged out and the screen was black. Tried just typing my password as I could see and move the mouse pointer and Beryl is installed. After 5 minutes decided to reboot, now the disk won't boot, it says insert boot disc.

Any ideas I'm in Windows now for the first time since I made the change just before xmas (Was about to delete the windows partition glad I didn't now as I lost my livecd.)

As soon as the livecd is down I shall burn it and try and have a look at my Ubuntu install make sure it's hardware related. Feels really wrong being back in windows, so bitterly slow and my Desktop is a nightmare and I miss my Gnome.

---

### Post by Shatrat on 2007-01-17
Dead hard drive?
Forbidden love gone wrong?  
Is windows on the same drive as ubuntu?

---

### Post by Tutu 1234 on 2007-01-17
Dead as in won't boot, got the livecd working.

This is the result of sudo fdisk -l

"Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table"

which is my Ubuntu install the NTFS one shows fine.

---

### Post by Bigbluecat on 2007-01-17
It looks like there has been some kind of disk corruption and the system cannot find the partition table for your Ubuntu partition.

You may be able to find and recover this with a program called TestDisk

[http://freshmeat.net/projects/testdisk/](http://freshmeat.net/projects/testdisk/)

I think it is available through synaptics but since you cannot boot Ubuntu that may not help.

Download the GParted liveCD and burn as an ISO. Boot from this and open a terminal to run TestDisk.

BE VERY CAREFUL. BACK UP EVERYTHING FIRST - EVEN WINDOWS

Messing with partition tables is not trivial.

However, I successfully used TestDisk to recover my windows drive after a crash corrupted the partition table. 

Please read up on the web about this first. Don't just dive in.

---

