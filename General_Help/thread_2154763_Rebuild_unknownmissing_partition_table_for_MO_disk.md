---
title: "Rebuild unknown/missing partition table for MO disk"
date: 2013-06-15
forum: General Help
---

### Post by CaptainValor on 2013-06-15
Hello all,

I am attempting to recover medical image files from a backup made onto a (magneto-optical) MO disk. The original backup software/hardware and exact image formats are both unknown, unfortunately.

The MO disk does not mount automatically on Windows, Linux, or OS X. In all situations the disk spins up and the drive shows activity, but no mountable volumes are detected by the OS. OS X's Disk Utility shows the proper size of the media (652 MB, or one side of the 1.3 GB disk), but nothing else.

 Here's what I've done so far in Ubuntu:

Found these resources:
[http://ubuntuforums.org/showthread.php?t=1697571](http://ubuntuforums.org/showthread.php?t=1697571)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

- Ran **testdisk** to analyze the entire disk in the drive, with no partition type selected. Analysis reports **read errors** in cylinder 1 and cylinders 300-311 of 311, and then does not identify any partitions

- Ran **ddrescue -nv -b 1024** to copy the readable contents of the disk to a **.dd **file on my hard disk. Same **read errors **appear at the very beginning (early cylinder), and then at the end of the disk (final cylinders).

- Ran **testdisk **again on the .dd file, and when using *Sun Solaris partition* it detects a single partition for the "Whole Disk", but when I try to use the "Write" option I get the error "Function write_part_sun not implemented."

- Ran **foremost** to attempt recovering files by header information, but this returns no recoverable files


I'm stumped. I know I need to recreate the partition table, but if testdisk isn't able to do this, I'm at a loss.

**Please help!** Thanks in advance.


MO disk details:
Sony CWO-1300B, write-once, 1024 bytes/sector

Hardware Configuration:
Sony Vaio Media Center PC
Ubuntu 8.04
Sony SMO-F551
Adaptec AHA-2930CU SCSI Controller

---

