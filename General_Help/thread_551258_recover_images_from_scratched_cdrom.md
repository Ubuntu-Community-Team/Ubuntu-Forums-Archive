---
title: "recover images from scratched cdrom"
date: 2007-09-14
forum: General Help
---

### Post by chris_nava on 2007-09-14
I know this is a long shot...  Please help if you can.
I'm trying to recover images from a scratched cdrom disk.
The disk was created as an HFS disk. (on a mac)
Unfortunately it's the thin metal media side of the disk that is scratched near the inner ring (which is the location of partition/FAT information IIRC.)
When I place the disk in the drive it is recognized as a BLANK disk (this is incorrect as i can clearly see that there is data on about 1/3 of the disk surface.)
The disk appears as /dev/hdb
Using dd to dump the contents of the disk results in a tiny file just 2048 bytes in size which appears to contain some partition information only. (It mentions "Apple_partition_map" and "Apple_HFS" among other junk.)

I have tried **ddrescue** as detailed here. (complete failure)
[http://ubuntuforums.org/showthread.php?t=221669&highlight=recover+scratched]("http://ubuntuforums.org/showthread.php?t=221669&highlight=recover+scratched")

**testdisk** shows the HFS partition and it's size but defaults to incorrect CHS data 1-1-1
Trying to recover the backup superblock reports:
Superblock
HFSP boot sector: Can't read superblock.
Bad

Backup superblock
HFSP boot sector: Can't read backup superblock.
Bad

---

### Post by chris_nava on 2007-09-14
Nevermind...
On a whim, I tried the disk in the Powerbook that created it and it came up as though nothing was wrong!
I guess the crdom drive in the laptop is more forgiving than the one on this old PC I use as a file server.

* wipes brow*  I sure dodged a bullet on this one.
:biggrin:

---

