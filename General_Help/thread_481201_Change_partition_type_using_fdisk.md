---
title: "Change partition type using fdisk"
date: 2007-06-22
forum: General Help
---

### Post by SteveF on 2007-06-22
For some reason a partition I have formatted as ext3 and storing data shows Linux Swap as the partition type in fdisk.  I want to change it to Linux.  So what I was going to do was to use fdisk to modify the partition type from 82 to 83.  I have two questions:

1) Will this affect the existing data on that partition?  I've backed up the data, but like everyone else I prefer not to have to restore if I don't have to.  SO need to plan out my time.
2) When it asks for the id of the partition, do I assume that when I listed the partitions, it was the correct order?  The reason I ask, is this partition shows as last (9th) and is mounted to sdb9, but on the drive it actually should be the 8th partition (if you go by start and end location).

Thanks,

Steve

---

### Post by r0ck80y on 2007-06-22
1) Just changing the id wont affect its contents if you can write to that partition now without any problems. Unmount that partition before u change its id. Change the label and then press 'w' and exit fdisk.

2)Is there some free space in between? Not really sure. Maybe you can post the fdisk output here.

---

### Post by SteveF on 2007-06-22
> **r0ck80y said:**
> 1) Just changing the id wont affect its contents if you can write to that partition now without any problems. Unmount that partition before u change its id. Change the label and then press 'w' and exit fdisk.

2)Is there some free space in between? Not really sure. Maybe you can post the fdisk output here.

Thanks for the help.

Here's the output of fdisk:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+   c  W95 FAT32 (LBA)
/dev/sdb2            1217       30515   235344217+   f  W95 Ext'd (LBA)
/dev/sdb5            1217       17020   126945598+   7  HPFS/NTFS
/dev/sdb6   *       17021       18236     9767488+  83  Linux
/dev/sdb7           18237       19452     9767488+  83  Linux
/dev/sdb8           30334       30515     1461883+  82  Linux swap / Solaris
/dev/sdb9           19453       30333    87401601   82  Linux swap / Solaris

If I choose 9 for the ID and it ends up being my regular swap drive (sdb8) can I switch back or will my swap be hosed?

Steve

---

### Post by r0ck80y on 2007-06-22
try first:```

sudo swapoff /dev/sdb9
```
If it says "swapoff: /dev/sdb9: Invalid argument", then sdb9 is not your swap and u can safely select 9 and change its label

---

### Post by SteveF on 2007-06-22
Thanks for the help.  Modifying the last one seems to have worked.

Steve

---

### Post by ma65p on 2008-06-05
Sorry for being an idiot. But how exactly would you change a partition ID? What are the commands and steps? I'm so not familiar with this. Thanks.

---

