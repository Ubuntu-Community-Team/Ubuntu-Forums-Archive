---
title: "Parted won't read my partition table, but fdisk does...why??"
date: 2008-05-30
forum: General Help
---

### Post by bpont on 2008-05-30
Fdisk:

```
sudo fdisk -l /dev/sdb

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d74fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          12       96358+  83  Linux
/dev/sdb2              13       12170    97659135    5  Extended
/dev/sdb3            6224       18249    96598845   83  Linux
/dev/sdb4           18250       30401    97610940   83  Linux
/dev/sdb5              13        6092    48837568+  83  Linux
/dev/sdb6            6093        6223     1052226   82  Linux swap / Solaris
```

Parted:
```

(parted) print                                                            
Error: Can't have overlapping partitions. 
```

I should also mention that I use lvm2 and have /dev/sdb3 and /dev/sdb4 as a volume group formatted with ext3 as the file system.

Here's the output of pvdisplay:

```
  --- Physical volume ---
  PV Name               /dev/sdb4
  VG Name               home
  PV Size               93.09 GB / not usable 3.18 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              23830
  Free PE               0
  Allocated PE          23830
  PV UUID               kxfNEJ-lj3j-YXsQ-D09j-B5lk-wRee-29Jvcc
   
  --- Physical volume ---
  PV Name               /dev/sdb3
  VG Name               home
  PV Size               92.12 GB / not usable 2.81 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              23583
  Free PE               0
  Allocated PE          23583
  PV UUID               8k4Nix-Q4SY-zBrm-G2yk-bCqV-4olv-S6MY3p
```

---

### Post by fjgaude on 2008-05-30
What does cfdisk and gparted say about that drive?

---

### Post by bpont on 2008-05-30
> **fjgaude said:**
> What does cfdisk and gparted say about that drive?

cfdisk reads the table accurately.  gparted shows the disk as 'unallocated space'

---

### Post by housam on 2008-05-30
Your partition table has a problem : 
you have an extended partition sdb2 starts at 13 and end up at 12170.
this extended partition has 3 logical partitions 
-sdb5 start at 13 end at6092
-sdb6 start at 6093 end at 6223
-sdb3 start at 6224 end at 18249 ( which is not logic - it should end at 12170 to be inside the extended partition) this is making the partitions overlapping.

---

### Post by bpont on 2008-05-30
> **housam said:**
> Your partition table has a problem : 
you have an extended partition sdb2 starts at 13 and end up at 12170.
this extended partition has 3 logical partitions 
-sdb5 start at 13 end at6092
-sdb6 start at 6093 end at 6223
-sdb3 start at 6224 end at 18249 ( which is not logic - it should end at 12170 to be inside the extended partition) this is making the partitions overlapping.

So how can I correct this without losing data on my lvm logical volume, which encompasses /dev/sdb3 and /dev/sdb4?  That logical volume is where I mount /home

---

### Post by housam on 2008-05-30
we have no issue with sdb4. for sdb3 you can use [[COLOR="Red"]_this guide_[/COLOR]]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html") through the terminal to correct it.

I think you'll going to delete it and create a new one instead with the correct numbers.

OR if you have Acronis , it could help repairing the partition.

---

### Post by fjgaude on 2008-05-30
Well, I don't know what to make of it... likely there is a byte or even bit that parted thinks is not right... fdisk has been around a long, long time and likely if it says the partitions are okay they are. But who knows?

If the drive acts okay, use it, but if not, then try to repair the partition table... I've never seen such a situation as yours.

Good luck.

---

