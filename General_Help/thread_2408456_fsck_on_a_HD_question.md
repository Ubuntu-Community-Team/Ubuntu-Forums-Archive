---
title: "fsck on a HD question"
date: 2018-12-18
forum: General Help
---

### Post by ra7411 on 2018-12-18
I ran fsck on a couple partitions which checked out ok, then I ran it on an HD and got the below - anyone know what any of this means?  ;-))

```
   root@ra-main:~# fsck /dev/sdbfsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


Found a dos partition table in /dev/sdb  
```

xx

---

### Post by yancek on 2018-12-18
fsck is run on filesystems which are on partitions.  You should be able to check the drive with the command below which checks anything found in fstab:

```
fsck -A /dev/sdb
```

More details at the link below.  Note that fsck can not be run on a mounted filesystem.

[https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/](https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/)

---

