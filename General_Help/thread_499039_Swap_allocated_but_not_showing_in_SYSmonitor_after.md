---
title: "Swap allocated but not showing in SYSmonitor after installation"
date: 2007-07-12
forum: General Help
---

### Post by Pathfinder007 on 2007-07-12
Hi I installed Ubuntu 7.04 on my laptop which is an old Acer TravelMate 280, P4M 1.8Ghz with 256mb DDR PC2100 memory. 
During the installation, I adequately allocated around 600mb of Swap partition, but after installation, when I checked the system monitor, the swap file was showing 0kb used out of 0kb usage. 
In other words, the system was not recognizing any swap partition at all. I checked in the partition manager again, and the swap partition was clearly there. 
Any ideas?

---

### Post by Ozeuss on 2007-07-12
post your fstab and partition table
```
cat /etc/fstab
```
```
sudo fdisk -l
```

---

### Post by Pathfinder007 on 2007-07-12
Partition is like this:

Primary partition -  " / " 8Gb 
Extended partition -  12Gb 
           - Logical partition " /home "  11Gb
           - Logical partition  linux-swap 650mb 

I am currently running Edgy because 7.04 had that problem, so I had to reinstall Edgy 
and fstab in Edgy is: 

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1033     8297541   83  Linux
/dev/hda2            1034        2432    11237467+   5  Extended
/dev/hda5            1034        2349    10570738+  83  Linux
/dev/hda6            2350        2432      666666   82  Linux swap / Solaris

I partition my drive like this for both versions of Ubuntu.

---

### Post by Ozeuss on 2007-07-12
You didn't post your fstab, so check it. "sudo gedit /etc/fstab"
 in edgy most entry might be if the UUID type. that might render your swap not working, for some reason.
so the line that deals with swap should be reverted to the normal naming method.
so instead of "UUID=F63CC0453CBFFF1D /media/hda6 swap ...something" change it to:
/dev/hda6 none swap sw 0 0.

then "sudo mount -a" or "sudo swapon -a"
that should make it work.

---

