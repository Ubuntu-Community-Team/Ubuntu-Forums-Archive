---
title: "adding a hdd"
date: 2007-03-24
forum: General Help
---

### Post by arya6000 on 2007-03-24
Hello

I have a HDD that I was using for windows, in DOS using fdisk I deleted all the partitions and made a new partition, But it doesn't show up in Ubuntu. What can I do so I can use it in Ubuntu? I'm just using this drive to add more space to my computer.


Thanks

---

### Post by mahiyar on 2007-03-24
Can you be more specific, when you say you cannot see, is it through live cd?  Do you have another disk having ubuntu? After booting in ubuntu, did you try to mount. Try >sudo fdisk -lu, can you see your disk there.

---

### Post by arya6000 on 2007-03-24
> **mahiyar said:**
> Can you be more specific, when you say you cannot see, is it through live cd?  Do you have another disk having ubuntu? After booting in ubuntu, did you try to mount. Try >sudo fdisk -lu, can you see your disk there.

I have had Ubuntu installed for about a year now and my HDD is running out of space, so I'm trying to add  one and the partition is fat32. When I types sudo fdisk -lu is does show up. But how can I formate it to the Linux file system?


Thanks

---

### Post by taurus on 2007-03-24
If you want to format a partition to ext3, just run (assuming it's _/dev/hdb1_)

```
sudo mke2fs -j /dev/hdb1
```

---

### Post by arya6000 on 2007-03-24
> **taurus said:**
> If you want to format a partition to ext3, just run (assuming it's _/dev/hdb1_)

```
sudo mke2fs -j /dev/hdb1
```

I did that and still this is what I get:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   117081719    58540828+  83  Linux
/dev/hda2       117081720   120101939     1510110    5  Extended
/dev/hda5       117081783   120101939     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   156296384    78148161    c  W95 FAT32 (LBA)


It shows that it is still a FAT32 File system

---

