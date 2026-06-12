---
title: "need help to explain my partitions after setting up dual boot"
date: 2007-09-11
forum: General Help
---

### Post by giboman on 2007-09-11
Here my problem, I set up a dual boot with Vista and Linux. I seem to have missed layed  some of my disk space. Below is a print out of my partitions. Can some one please explain to me what exactly I am looking at and how can I retrieve my disk space for Ubuntu.
I am presuming that  Vista is /dev/sda3 and Linux is /dev/sda8
Any help would be appreciated.:confused:



root@hugh-linux:~# /sbin/fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12        1317    10485760    7  HPFS/NTFS
/dev/sda3   *        1317        9560    66210937+   7  HPFS/NTFS
/dev/sda4            9561       19458    79498293+   f  W95 Ext'd (LBA)
/dev/sda5           19197       19458     2096128   dd  Unknown
/dev/sda6           12823       12835      104359+  83  Linux
/dev/sda7           12836       19196    51094701   8e  Linux LVM
/dev/sda8   *        9561       12681    25069401   83  Linux
/dev/sda9           12682       12822     1132551   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by merlinus on 2007-09-11
Exactly what did you do to partition your hdd.

---

### Post by eggdeng on 2007-09-11
I work it out as

dev/sda1 88MB Dell Utility
/dev/sda2 10GB 7 WIN
/dev/sda3 66GB WIN
Total 76+GB

/dev/sda4 79GB ?? EXTENDED partition which contains

/dev/sda5 2GB dd Unknown
/dev/sda6 104 MB Linux
/dev/sda7 51GB Linux
/dev/sda8 25GB Linux
/dev/sda9 1GB SWAP
Total 79+GB

Which is 155+GB, close enough to 160GB

Download the gparted live CD to get a better look.

---

### Post by louieb on 2007-09-11
go into system>administration>synaptic and install GParted. 
Then fire it up it will be in the system>administration menu  and post a screen shot. Its just easier to figure out whats going on that way.
Yea eggdeng's suggestion of getting the GParted live CD is a good one too.

---

### Post by ajgreeny on 2007-09-11
I think the layout of your disk is as follows, with a few uncertainties:-
**sda1** is a restore utility partition for vista.
**sda2** & **sda3** are both ntfs partitions for dells oem install of vista, presumably one for your docs and one for the system.
**sda4** & **sda5** are a mystery to me, but it almost looks as though windows 95 is implicated in **sda4,** which is also an extended partition.
**sad6** **sda7** & **sda8** are all linux partitions, with **sda8** as the bootable partition, but why there are three I don't know.
**sda9** is swap, no problem here.

It might be easier to see exactly what's what if you look with gparted, as it will show immediately which are extended partitions and what those actually contain, however, as merlinus says it would help to know what you did to get to this situation.  Don't forget you can only have four primary partitions on one disk, so there must be several partitions inside one or more extended partitions on your disk.

---

### Post by giboman on 2007-09-11
Thank you to everyone for there help.
I have attached a Screenshot of GParted. I presume /dev/sda7 is not being used, how can i give
this space to ubuntu

---

### Post by louieb on 2007-09-11
Why is sda7 an LVM (logical volume management)? 
Easiest thing to do is use GParted  and format it ext3. Then  look at the psychocats link in signature it has a mount Linux how to. And use it for a data partition.

---

