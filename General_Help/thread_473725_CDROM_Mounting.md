---
title: "CDROM Mounting"
date: 2007-06-14
forum: General Help
---

### Post by Damanther on 2007-06-14
I am having a problem mounting my DVD/CDRW and CDROM drives.

I'll start with the CD drive.

When I insert the disk, I get a window telling me that it is mounting /media/cdrom1 but the progress bar never goes past 0% and nothing actually gets mounted(that I can find).

Here is my dmesg output after inserting the CD

52339.514946] ISOFS: changing to secondary root
[52345.745755] hdd: command error: status=0x51 { DriveReady SeekComplete Error }
[52345.745765] hdd: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[52345.745769] ide: failed opcode was: unknown
[52345.947807] hdd: error code: 0x70 sense_key: 0x05 asc: 0x64 ascq: 0x00
[52345.947815] end_request: I/O error, dev hdd, sector 33128
[52345.948056] ISOFS: unable to read i-node block

and here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=d87414f7-6877-4043-8ee5-866d088115fe / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda5
UUID=9031676c-7061-4b0b-8c9a-b4528ddf6ef0 none swap sw 0 0
/dev/hdc /media/cdrom0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0

Any help is appreciated.

---

