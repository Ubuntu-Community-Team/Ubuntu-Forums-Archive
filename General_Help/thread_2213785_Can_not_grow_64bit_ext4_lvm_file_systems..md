---
title: "Can not grow 64bit ext4 lvm file systems."
date: 2014-03-28
forum: General Help
---

### Post by zircon009 on 2014-03-28
I am having difficulties growing a 64bit EXT4 logical volume partition from 18TB to 19TB.  I have the LV extended and run the resize2fs command and it acts like its stuck.  It does not show any error and I have let it run for days. I just get the resize2fs and version, nothing else shows up.   What am I doing incorrectly?  I have done this countless times with xfs, just not with ext4.  I am running Ubuntu 13.10(Saucy) x64.  I am using 14.10(trusty) e2fsprog and libs, since you need to be running 1.42.9 or later, and 13.10(Saucy) was defaulting to 1.42.7 which has several nasty 64bit ext4 bugs. All my drives are sata seagate 3tb drives. All 10 are connected to a sas pass through controller, running mdadm raid 5. All the drives are connected to one of two chenbro 36 port sas expanders. I have no trouble with accessing the files on the device, I just can not expand the file system. To add 1TB on the old XFS drives would normally take roughly 10 minutes. I have tried to do this operation both mounted and unmounted.  Thanks again.. Justin

# resize2fs /dev/mapper/vgfstore2-lvfstore2
resize2fs 1.42.9 (4-Feb-2014)

# resize2fs -p /dev/mapper/vgfstore2-lvfstore2
resize2fs 1.42.9 (4-Feb-2014)

# dpkg --list | grep e2
ii  e2fslibs:amd64                       1.42.9-3ubuntu1                     amd64        ext2/ext3/ext4 file system libraries
ii  e2fsprogs                            1.42.9-3ubuntu1                     amd64        ext2/ext3/ext4 file system utilities


Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent 64bit flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    user_xattr acl

#fsck.ext4 -p /dev/mapper/vgfstore2-lvfstore2
/dev/mapper/vgfstore2-lvfstore2: clean, 11552/301989888 files, 4383657996/4831838208 blocks

# cat preferences
Package: e2fsprogs
Pin: release n=trusty
Pin-Priority: 990

Package: e2fslibs
Pin: release n=trusty
Pin-Priority: 990

Package: e2fsck-static
Pin: release n=trusty
Pin-Priority: 990

Package: unrar
Pin: release n=trusty
Pin-Priority: 990

Package: *
Pin: release n=saucy
Pin-Priority: 900

Package: *
Pin: release o=Ubuntu
Pin-Priority: -10


# lvdisplay /dev/mapper/vgfstore2-lvfstore2
  --- Logical volume ---
  LV Path                /dev/vgfstore2/lvfstore2
  LV Name                lvfstore2
  VG Name                vgfstore2
  LV UUID                haVod0-2mVm-B1hL-IqO3-B8UZ-FeH5-SOVM6W
  LV Write Access        read/write
  LV Creation host, time fserve, 2013-06-06 13:23:24 -0500
  LV Status              available
  # open                 1
  LV Size                19.00 TiB
  Current LE             4980836
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     9216
  Block device           252:4

# vgdisplay vgfstore2
  --- Volume group ---
  VG Name               vgfstore2
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  77
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                5
  Open LV               5
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               24.56 TiB
  PE Size               4.00 MiB
  Total PE              6438571
  Alloc PE / Size       5014116 / 19.13 TiB
  Free  PE / Size       1424455 / 5.43 TiB
  VG UUID               Xq4ls2-y4h2-xwNP-FOA9-xDhQ-sehi-l5aB1d

---

### Post by zircon009 on 2014-08-02
I just wanted to post a update to this problem, in case someone runs across this problem via google or some other search engine.  I let the resize filesystem job run for around three months and decided to throw the towel in on EXT4 64bit file system. Please note that I am not talking about the default EXT4 32bit file system. With all the major bugs the 64bit portion of the program, its obviously not ready for prime time yet.  I just finished converting ~30TB to xfs, which I have used before. With XFS I can add a 1 TB to a mounted file system in around 2-3 minutes on a bad day. I guess the only thing I do not like about it, is I have to setup a cron defrag job, or it will get massively fragmented with time. The machine is also connected to a battery backup, which the machine monitors.

---

