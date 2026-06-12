---
title: "System hung, 14.04 LTS"
date: 2014-10-30
forum: General Help
---

### Post by MannyL on 2014-10-30
I have a home built PC with three hard drives. One is a SSD and the other two are standard hard drives. One with an IDE interface and one with a SATA interface.

SMART says all the drives are good. I'm not sure though because if I am doing anything somewhat intensive my screen goes blank. Sometimes it's a white screen other times purple. I know the system is hung because I can't even SSH in from a windows system on my home network.

I doubt it's a memory issue because I ran memtest off the flash drive I used to install the OS and it passed after running for 24 hours.

How can I start to diagnose the problem, and then fix it?

---

### Post by ibjsb4 on 2014-10-31
You could monitor your system resources, see if anything is eating them up.
```
top
```
Right-click on the title bar and check 'always on top', then make it lock up.

---

### Post by MannyL on 2014-11-01
I tried that and the screen goes blank to quickly to see anything

---

### Post by ibjsb4 on 2014-11-01
Ok, so much for that :)

Try looking here for clues:
/var/crash/.crash
/var/log/dmesg

---

### Post by MannyL on 2014-11-03
> **ibjsb4 said:**
> Ok, so much for that :)

Try looking here for clues:
/var/crash/.crash
/var/log/dmesg

There is no .crash in /var/crash and I don't see anything abnormal in /var/log/dmesg


I realised if I use one of my windows boxes to ssh in I can run TOP and have the the ssh info still on screen at the crash.

I tried to benchmark the drives to put a load on the system and it threw an error. I then opened a terminial and tried sudo fdisk -lu and the output looks weird
```


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088bc2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   234440703   116969473    5  Extended
/dev/sda5          501760   234440703   116969472   8e  Linux LVM

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x08724622

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907029167  1953514552+  83  Linux
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976771054   488385496   83  Linux

Disk /dev/mapper/ubuntu--vg-root: 111.7 GB, 111719481344 bytes
255 heads, 63 sectors/track, 13582 cylinders, total 218202112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 8053 MB, 8053063680 bytes
255 heads, 63 sectors/track, 979 cylinders, total 15728640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
emanuel@UbuntuPC:~$ 


```

So how do I fix this issue?

---

