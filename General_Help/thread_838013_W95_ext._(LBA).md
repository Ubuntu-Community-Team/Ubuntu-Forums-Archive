---
title: "W95 ext. (LBA) ???"
date: 2008-06-23
forum: General Help
---

### Post by dracayr on 2008-06-23
hi,

I seem to have a partition on my computer that I didn't know of:

```
/dev/sda2            3649        6138    20000925    f  W95 Erw. (LBA)
```

I can't mount the partition ("you have to specify the file system type"), and I can't format it

```
mke2fs 1.40.8 (13-Mar-2008)
mke2fs: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).
```

This is on a laptop which was bought with xp installed, so I have no Idea where a W95 partition would come from...


EDIT: Oh, and fdisk doesn't work either

```
dracayr@dracayr-lab:~$ sudo fdisk /dev/sda2

Unable to read /dev/sda2
```

My question is, how do I format,remove or mount it?

dracayr

---

### Post by cariboo on 2008-06-23
It may be a restore partition. A lot of laptop manufacturers don't like to  supply cd's when they sell laptops. they put all the files you need to restore your laptop to shiny new condition on a hidden partition.

I think you should think twice before deleting the partition.

Jim

---

### Post by dracayr on 2008-06-23
I installed gparted and there it I could see that it is an extended partition, that has the two logical partitions /home and swap.. :)

dracayr

---

