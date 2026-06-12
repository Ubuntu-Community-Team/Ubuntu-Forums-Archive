---
title: "major and minor values to create disk partition device files"
date: 2008-02-18
forum: General Help
---

### Post by activo1969 on 2008-02-18
Hi

my box has 4 HD: 3 IDE and 1 SATA.

The disk device files are:

[FONT="Courier New"]/dev/hda
/dev/hdb
/dev/hdc   # CD-ROM
/dev/hdd[/FONT]

/dev/sda  # SATA disk

My problem is I cannot access /dev/hda partitions because the disk device files (/dev/hda*) are not found.

I created /dev/hda3 and /dev/hda5 by means of mknod command, but I cannot mount those partitions. I guess the minor and major number are wrong, but I found NO guide for help (all other HD partitions are properly mounted)

May you help me ?

P.D: FDISK command shows the HD /dev/hda contains /dev/hda3 and /dev/hda5 (extended partition), i.e., /dev/hda1, /dev/hda2 and /dev/hda4 DON'T EXIST.

---

### Post by geraldm on 2008-02-18
The documentation is in the Linux source, topdir/Documentation/devices.txt
from that file:
      0 = /dev/hda    Master: whole disk (or CD-ROM)
     64 = /dev/hdb    Slave: whole disk (or CD-ROM)

    For partitions, add to the whole disk device number:
      0 = /dev/hd?    Whole disk
      1 = /dev/hd?1   First partition
      2 = /dev/hd?2   Second partition
        ...
     63 = /dev/hd?63  63rd partition

    For Linux/i386, partitions 1-4 are the primary
    partitions, and 5 and above are logical partitions.
--end quote
The major for the above is 3 (block); it is the minors that are shown above.
You should end up with something similar to this for hda3
ls -l 
brw-rw---- 1 root disk 3,  3 2005-04-01 08:37 /dev/hda3

Gerald

---

### Post by activo1969 on 2008-02-20
I know the theory but

[INDENT]
[FONT="Courier New"][COLOR="Blue"]
# fsdisk -l /dev/hda
omitting empty partition (5)

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f512f50

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2            2561       14946    99490545    f  W95 Ext'd (LBA)
/dev/hda3               1        2560    20563168+   7  HPFS/NTFS
/dev/hda5            4812        8989    33559753+   7  HPFS/NTFS

**Partition table entries are not in disk order**
[/COLOR][/FONT]

[COLOR="Blue"][FONT="Courier New"]
# ls -l /dev/hda*
brw-rw---- 1 root disk 3, 0 Feb 20  2008 /dev/hda
brw-rw---- 1 root disk 3, 1 Feb 20 19:58 /dev/hda1
brw-rw---- 1 root disk 3, 2 Feb 20 19:59 /dev/hda2
brw-rw---- 1 root disk 3, 3 Feb 20 19:59 /dev/hda3
brw-rw---- 1 root disk 3, 4 Feb 20 19:59 /dev/hda4
brw-rw---- 1 root disk 3, 5 Feb 20 19:59 /dev/hda5
[/FONT][/COLOR]

[FONT="Courier New"][COLOR="Blue"]
# mount /dev/hda3 /mnt
mount: /dev/hda3 is not a valid block device
[/COLOR][/FONT]
[/INDENT]


Should I reconfigure the partition table ?

---

