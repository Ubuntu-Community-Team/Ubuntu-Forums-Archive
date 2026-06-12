---
title: "[SOLVED] Cannot Mount Volume - External Hard Drive"
date: 2008-06-14
forum: General Help
---

### Post by bric on 2008-06-14
I've got an old external hard drive (well, old by computer standards -- 80GB) that won't mount properly.  It was originally used with Windows (fat32) then I reformated as ext2 (if I recall correctly) as fat32 was giving me problems with large files (>2gb).

The Ubuntu system is Hardy Heron 64bit.

Now when I try to connect I get:
> 
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

fdisk -l worryingly (because of the fat32) shows this:
> 
Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0552ec1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10011    80413326    b  W95 FAT32


I've tried manually mounting with vfat and ext2
> 
me@thecomputer:~$ sudo mount -t vfat /dev/sdb1 /mnt/externalhd/
mount: /dev/sdb1: can't read superblock

me@thecomputer:~$ sudo mount -t ext2 /dev/sdb1 /mnt/externalhd/
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Judging from those 2 errors it seems the system is trying to automatically mount as ext2 (which is what I remember reformatting with).

sudo fsck /dev/sdb1 gives me this:
> fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Group descriptors look bad... trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


I tried e2fsck exactly as suggested ...
sudo e2fsck -b 8193 /dev/sdb1
> e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb1
Filesystem mounted or opened exclusively by another program?



also, dmesg | tail
> [24541.842838] EXT2-fs: group descriptors corrupted!
[24688.343416] EXT2-fs error (device sdb1): ext2_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[24688.343423] EXT2-fs: group descriptors corrupted!
[24711.504860] EXT2-fs error (device sdb1): ext2_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[24711.504866] EXT2-fs: group descriptors corrupted!
[25012.629117] FAT: Filesystem panic (dev sdb1)
[25012.629121]     invalid access to FAT (entry 0x00c00008)
[25012.629124]     File system has been set read-only
[25023.190742] EXT2-fs error (device sdb1): ext2_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[25023.190750] EXT2-fs: group descriptors corrupted!


and 
blkid
> /dev/sdb1: UUID="bb249ede-2c5a-430f-a952-de9b7e6e126d" TYPE="ext2" 

and
lsusb
> 
<snip />
Bus 007 Device 005: ID 059b:007e Iomega Corp.
<snip />


I've googled but still am uncertain (as a beginner) about how best to proceed, not knowing which suggestions might be irreversible in the damage they might cause to the data.... and I haven't seen too many suggestions where people said, "Oh great that fixed it".

Any suggestions are welcome.

---

### Post by bric on 2008-08-01
In case it helps someone, I eventually used testdisk (available on the partmagic livecd or just from commandline in ubuntu hardy if, like me, you have an external HD with the problem) to restore the ext2 file system as it should have been.

hurray! case closed.

---

### Post by AlecJ on 2010-05-15
Thank you
This info just got me out of trouble.

---

