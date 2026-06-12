---
title: "GParted unrecognised disk label (SSD)"
date: 2013-06-19
forum: General Help
---

### Post by monicaC on 2013-06-19
Hi, I have a Kingston 64GB SSD that I am having problems with. I think something is wrong with the partition table.  I tried formatting/creating a new partition in Win 7, but could not.  Now I am using GParted in Ubuntu.

It shows: "No partition table found on device" and the warning "unrecogised disk label". 
When I try to create a partition table, it looks like its working but nothing happens.

sudo parted /dev/sda unit s print
Error: /dev/sda: unrecognised disk label
Model: ATA KINGSTON SNV425S (scsi)                                        
Disk /dev/sda: 125045424s
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Help please.

---

### Post by oldfred on 2013-06-19
Does testdisk show anything better, like old partitions?

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

