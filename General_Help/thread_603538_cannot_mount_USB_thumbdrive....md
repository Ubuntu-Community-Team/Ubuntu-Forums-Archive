---
title: "cannot mount USB thumbdrive..."
date: 2007-11-05
forum: General Help
---

### Post by spotdog14 on 2007-11-05
Ok, i know this topic has been brought up before, but i cannot seem to find an answer that works for me. 

I cannot get my Gusty system to mount USB thumbdrives, any thoughts?

---

### Post by spotdog14 on 2007-11-05
oh by the way this is my fdisk -l output:

> spotdog14@Asus-S5n:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3020        4499    11888100   83  Linux
/dev/sda2   *         244        3019    22298220    7  HPFS/NTFS
/dev/sda3            4500        4864     2931862+  83  Linux
/dev/sda4               1         243     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order


Also here is my dmesg:

> [ 1120.688000] Initializing USB Mass Storage driver...
[ 1120.688000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1120.692000] usb-storage: device found at 11
[ 1120.692000] usb-storage: waiting for device to settle before scanning
[ 1120.692000] usbcore: registered new interface driver usb-storage
[ 1120.692000] USB Mass Storage support registered.
[ 1125.692000] usb-storage: device scan complete
[ 1125.696000] scsi 2:0:0:0: Direct-Access     CREATIVE NOMAD_MUVO       0001 PQ: 0 ANSI: 4
[ 1125.700000] sd 2:0:0:0: [sdb] 256001 512-byte hardware sectors (131 MB)
[ 1125.704000] sd 2:0:0:0: [sdb] Write Protect is off
[ 1125.704000] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 04
[ 1125.704000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1125.716000] sd 2:0:0:0: [sdb] 256001 512-byte hardware sectors (131 MB)
[ 1125.720000] sd 2:0:0:0: [sdb] Write Protect is off
[ 1125.720000] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 04
[ 1125.720000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1125.720000]  sdb: sdb1
[ 1125.724000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1125.724000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 1126.108000] end_request: I/O error, dev sdb, sector 256000
[ 1126.108000] Buffer I/O error on device sdb, logical block 256000


---

### Post by spotdog14 on 2007-11-05
come on someone must have an answer for me?

---

