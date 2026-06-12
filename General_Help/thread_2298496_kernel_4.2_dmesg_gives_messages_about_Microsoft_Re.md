---
title: "kernel 4.2: dmesg gives messages about Microsoft Reserved (MSR) partition"
date: 2015-10-11
forum: General Help
---

### Post by sanderj on 2015-10-11
I'm running Linux 4.2.3-040203-generic on Ubuntu 15.04. My dmesg says in red (thus error):

```

$ dmesg -l err

[  122.264548] EXT4-fs (mmcblk0p2): VFS: Can't find ext4 filesystem
[  122.267371] EXT4-fs (mmcblk0p2): VFS: Can't find ext4 filesystem
[  122.270148] EXT4-fs (mmcblk0p2): VFS: Can't find ext4 filesystem
[  122.273031] FAT-fs (mmcblk0p2): bogus number of reserved sectors
[  122.273044] FAT-fs (mmcblk0p2): Can't find a valid FAT filesystem
[  122.281899] XFS (mmcblk0p2): Invalid superblock magic number
[  122.287514] FAT-fs (mmcblk0p2): bogus number of reserved sectors
[  122.287521] FAT-fs (mmcblk0p2): Can't find a valid FAT filesystem
[  122.295252] VFS: Can't find a Minix filesystem V1 | V2 | V3 on device mmcblk0p2.
[  122.303993] hfsplus: unable to find HFS+ superblock
[  122.306911] qnx4: no qnx4 filesystem (no root dir).
[  122.309509] ufs: You didn't specify the type of your ufs filesystem

mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...

>>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[  122.309804] ufs: ufs_fill_super(): bad magic number
```

```
$ sudo fdisk  -l /dev/mmcblk0 | grep 0p2
/dev/mmcblk0p2   534528   796671   262144  128M Microsoft reserved
```

It's probably the MSR; see [https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

So: should I just ignore the dmesg info, or can I do some setting to avoid the dmesg error message?

---

