---
title: "fstab for external usb with fat32 and ext3"
date: 2007-02-25
forum: General Help
---

### Post by martal on 2007-02-25
My external USB (LaCie 250GB) sucessfully mounts the FAT32/vfat partition on it using plug 'n play.

But it doesn't mount the ext3 partition. I have to manually mount this.

What line should I have in fstab? Or is this the wrong approach and I should be automating a manual mount?

According to GParted:
FAT32 partition /dev/sda5, mount point is /media/LaCie32
Ext3 partition /dev/sda6, no current mount point, but want it to /media/LaCieExt3

Strangely, after first setting up the ext3 partition, Ubuntu saw both partitions. Now it sees only the FAT32.

---

