---
title: "Merging Harddisk Parttions"
date: 2007-03-01
forum: General Help
---

### Post by oneofth3m on 2007-03-01
hi,

I have recently started using Ubuntu and i would like to know how partitions in my harddisk could be merged?  i used to perform this task in windows using acronis partition manager can i know how to do it linux? I donot want to lose my data that is residing on various partitions. I would like to merge hdb5,hdb6,hdb7,hdb8 which are continuos on hard disk and all are FAT32. i have listed my partitions table entries below.

Specs:

_uname -a _
Linux nubuntu 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686 GNU/Linux

_lb_release -a_
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper

_fdisk -l_
Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1567    12586896    7  HPFS/NTFS
/dev/hdb2            1568        9729    65561265    f  W95 Ext'd (LBA)
/dev/hdb5            1568        3712    17229681    b  W95 FAT32
/dev/hdb6            3713        4364     5237158+   b  W95 FAT32
/dev/hdb7            4365        6796    19535008+   b  W95 FAT32
/dev/hdb8            6797        7296     4016218+   b  W95 FAT32
/dev/hdb9            8712        9729     8177053+  83  Linux
/dev/hdb10           7297        7418      979933+  82  Linux swap / Solaris
/dev/hdb11           7419        8711    10385991   83  Linux

Partition table entries are not in disk order

---

### Post by dbqp on 2007-03-01
Have you tried gparted? IT can be found [here]("http://gparted.sourceforge.net/")

Run it live and all your partitions will be "unmounted" and able to be moved/copied/resized/etc...

I would definitely suggest reading the documentation before doing ANY resizing/merging. And back up!

I believe a new version was just released???

My two cents...hope it helps.

---

### Post by oneofth3m on 2007-03-01
Thanks for the reply.

I wanted to merge two partitions, with gparted to do this i should have unallocated regions. 

The resize operation can only reduce the size of the parttion and can increase only if theres unallocated space after it. Atleast from the options available and documentation provided this is what i concluded. Correct me if i am wrong.

---

### Post by bodhi.zazen on 2007-03-01
I am not sure, but you might want to look at LVM :

[http://www-128.ibm.com/developerworks/linux/library/l-lvm/](http://www-128.ibm.com/developerworks/linux/library/l-lvm/)

[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)

---

### Post by oneofth3m on 2007-03-02
Thanks for the replies.

I have gone through the forums of gparted and learnt that MERGING is still in feature requests. I manually did some copying...resizing and moving to merge the partions. An automatic tool would be helpful.

Anywayz thanks

---

