---
title: "Need help with reassemble raid 1 using mdadm"
date: 2015-04-09
forum: General Help
---

### Post by Walter_ZAMBOTTI on 2015-04-09
Drive is one from a mirrored pair out of a ReadyNAS RNDU2000 (2 drive unit).  This drive uses 16K file system block size.

I have it attached via a USB<->SATA adapter.

Fdisk sees the device as /dev/sdb1 (GPT)

# file -sL /dev/sdb1
/dev/sdb1:Linux Software Raid version 1.2 (1) UUID=d0...b0 name=A0...3A:0 level=1 disks=2

Attempted to reassemble from one drive (force assemble with only one member with --run):

# mdadm --assemble --run /dev/md0 /dev/sdb1
mdadm: cannot re-read metadata from /dev/sdb1 - aborting

Attempted normal mount:

# mount -o ro /dev/sdb1 /mnt/drive
mount: unknown filesystem type 'linux_raid_member'
 
Attempted to fuse mount drive:

# mkdir /mnt/drive
# fuseext2 -o ro,allow_other /dev/sdb1 /mnt/drive
... Probe failed [main (fuse-ext2.c:347)]

Tried to scan for volume groups:

# vgscan
...
No volume groups found

I'm using Ubuntu 14.04LTS
fuse-ext2 version '0.4', fuse_version:'29'

Any ideas how I can mount and access this drive?

---

