---
title: "Hide volume /var from the desktop"
date: 2014-04-26
forum: General Help
---

### Post by coldraven on 2014-04-26
I just replaced Xubuntu 13.10 with 14.04 on my Asus eeePC 900.
It has two SSDs, a 4GB for the system and a 16GB for data. As the small drive tends to get full I had moved /tmp and /var to their own partitions on the 16GB drive and it all worked nicely.
Now I'm seeing the /var volume on the desktop. I kept a copy of the old fstab and it seems to be identical to the new one so I do not understand why this is happening.
Any ideas?

The small "BIOS" partition is hidden and is for the "Boot Boost" function of this laptop. Mounted at /mnt/asusbios
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=013d9717-e74f-490e-8e60-2a8eede9beda /               ext4    errors=remount-ro 0       1
# /tmp was on /dev/sdb1 during installation
UUID=0493c020-b281-4b71-956e-d3df67fd0477 /tmp            ext4    defaults        0       2
# /var was on /dev/sdb5 during installation
UUID=8fbbf24a-5210-4024-8238-71b4f842c527 /var            ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=7f57e555-fa86-4fa7-bd68-e3045adecb8b none            swap    sw              0       0
LABEL=BIOS    /mnt/asusbios    vfat    noauto    0    0
```

```

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003eaaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     7837695     3917824   83  Linux
/dev/sda3         7839720     7855784        8032+   c  W95 FAT32 (LBA)
/dev/sda4         7855785     7871849        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006bf64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    25616383    12807168   83  Linux
/dev/sdb2        25618430    31520767     2951169    5  Extended
/dev/sdb5        27617280    29569023      975872   83  Linux
/dev/sdb6        29571072    31520767      974848   83  Linux
/dev/sdb7        25618432    27617279      999424   82  Linux swap / Solaris

Partition table entries are not in disk order

```

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   3.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   3.8G  0 part /
&#9500;&#9472;sda3   8:3    0   7.9M  0 part 
&#9492;&#9472;sda4   8:4    0   7.9M  0 part 
sdb      8:16   0    15G  0 disk 
&#9500;&#9472;sdb1   8:17   0  12.2G  0 part /tmp
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9500;&#9472;sdb5   8:21   0   953M  0 part /var
&#9500;&#9472;sdb6   8:22   0   952M  0 part 
&#9492;&#9472;sdb7   8:23   0   976M  0 part [SWAP]
```

---

### Post by ajgreeny on 2014-04-26
It's probably nothing to do with fstab but possibly that you have set **Desktop Settings** to show Removable Devices/Volumes in the Icons tab.

---

### Post by coldraven on 2014-04-26
> **ajgreeny said:**
> It's probably nothing to do with fstab but possibly that you have set **Desktop Settings** to show Removable Devices/Volumes in the Icons tab.

If so then I should be seeing the /tmp partition on the desktop. As it is I only see the /var partition and any removable drives.
So I'm still baffled at the moment.

---

### Post by ajgreeny on 2014-04-26
Good point!

In which case I'm as baffled as you are.  Sorry.

---

### Post by pqwoerituytrueiwoq on 2014-04-26
are you sure you have the uuid right for /var?

---

### Post by coldraven on 2014-05-04
Sorry that I did not respond but I'm working away from home for a while and don't have the eeePC with me. In fact I gave it to a friend but I will try to sort it out for him when I return.

On the plus side I bought a Toshiba NB100 netbook for £30. It's in mint condition and is running Xubuntu 14.04 really nicely.
When I get back home I'm going to swap the HDD for a SSD and max out the memory.

---

