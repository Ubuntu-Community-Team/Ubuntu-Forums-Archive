---
title: "Recover data from bad drive in a RAID configuration"
date: 2014-12-20
forum: General Help
---

### Post by mark_s2 on 2014-12-20
I had two drives in a server in a mirror RAID configuration.  A few months ago I replaced the power supply, but after replacing it, I found out that the server has been running only off one drive because the SATA cable was loose on the second drive.  Now it appears the first drive is failing, and I'm trying to either 1) recover the data from the failing drive or 2) recover the data (even if partially lost) from the other drive that was not hooked up properly.

I have the failing drive hooked up to another machine and booting into Ubuntu off a USB drive.  I am trying to mount the drive to see if I'm able to copy the files off to another drive, but I'm unable to mount it.  I'll admit I'm not the best at working with RAID configs :)  Any help is greatly appreciated!

Output of fdisk -l

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
```

parted:

```
root@ubuntu:~# parted /dev/sdb print
Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  2000GB  2000GB                     raid
```

fsck:

```
root@ubuntu:~# fsck /dev/sdb1
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


```

---

