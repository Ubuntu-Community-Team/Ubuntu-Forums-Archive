---
title: "external hdd can't read superblock"
date: 2007-02-26
forum: General Help
---

### Post by jude999 on 2007-02-26
Hi again.
I was around yesterday trying to mount my newly bought ntfs usb 2.5" hard drive and failed miserably.
As I could not format it on my ubuntu computer ("error while setting new disklabel"), I formated it today in fat32 at the office, on a windows machine.

But absolutely nothing has changed... still cant mount it and It gives me the same information.
In gparted, it sees it as unallocated space.

Here is the output of some commands before you ask:

```
simon@simon:~$ ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 2007-02-26 20:33 ata-IC25N040ATMR04-0_MRG254KBD9S2TP -> ../../hda
lrwxrwxrwx 1 root root 10 2007-02-26 20:33 ata-IC25N040ATMR04-0_MRG254KBD9S2TP-part1 -> ../../hda1
lrwxrwxrwx 1 root root 10 2007-02-26 20:33 ata-IC25N040ATMR04-0_MRG254KBD9S2TP-part5 -> ../../hda5
lrwxrwxrwx 1 root root  9 2007-02-26 20:43 usb-SAMSUNG_HM120JC_?????????? -> ../../sda

```
sda is the one I am trying to mount

```
simon@simon:~$ sudo mount -t vfat /dev/sda /mnt/usbdisk
mount: /dev/sda: can't read superblock

```

```
simon@simon:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4687    37648296   83  Linux
/dev/hda2            4688        4864     1421752+   5  Extended
/dev/hda5            4688        4864     1421721   82  Linux swap / Solaris

```
Not mounted

```
[17180276.420000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180276.420000] end_request: I/O error, dev sda, sector 0
[17180276.424000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180276.424000] end_request: I/O error, dev sda, sector 0
[17180276.456000] JFS: nTxBlock = 3777, nTxLock = 30221
[17180276.468000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180276.468000] end_request: I/O error, dev sda, sector 64
[17180276.472000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180276.472000] end_request: I/O error, dev sda, sector 120
[17180276.480000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180276.480000] end_request: I/O error, dev sda, sector 64
[17180276.484000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180276.484000] end_request: I/O error, dev sda, sector 120
[17180504.112000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180504.112000] end_request: I/O error, dev sda, sector 0
[17180504.112000] printk: 7 messages suppressed.
[17180504.112000] Buffer I/O error on device sda, logical block 0
[17180504.116000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180504.116000] end_request: I/O error, dev sda, sector 0
[17180504.116000] Buffer I/O error on device sda, logical block 0
[17180504.124000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180504.124000] end_request: I/O error, dev sda, sector 0
[17180504.124000] Buffer I/O error on device sda, logical block 0
[17180504.128000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180504.128000] end_request: I/O error, dev sda, sector 8
[17180504.128000] Buffer I/O error on device sda, logical block 1
[17180504.144000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180504.144000] end_request: I/O error, dev sda, sector 16
[17180504.144000] Buffer I/O error on device sda, logical block 2
[17180504.152000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180504.152000] end_request: I/O error, dev sda, sector 24
[17180504.152000] Buffer I/O error on device sda, logical block 3
[17180504.156000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180504.156000] end_request: I/O error, dev sda, sector 0
[17180504.156000] Buffer I/O error on device sda, logical block 0
[17180731.116000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17180731.116000] end_request: I/O error, dev sda, sector 0
[17180731.120000] FAT: unable to read boot sector
[17181742.156000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17181742.156000] end_request: I/O error, dev sda, sector 0
[17181742.156000] FAT: unable to read boot sector
[17182258.680000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17182258.680000] end_request: I/O error, dev sda, sector 0
[17182258.684000] FAT: unable to read boot sector
[17182750.632000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17182750.632000] end_request: I/O error, dev sda, sector 0
[17182750.632000] FAT: unable to read boot sector
[17182794.284000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17182794.284000] end_request: I/O error, dev sda, sector 0
[17182794.284000] Buffer I/O error on device sda, logical block 0
[17182794.288000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17182794.288000] end_request: I/O error, dev sda, sector 0
[17182794.288000] Buffer I/O error on device sda, logical block 0
[17182794.316000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17182794.316000] end_request: I/O error, dev sda, sector 0
[17182794.316000] Buffer I/O error on device sda, logical block 0
[17182794.336000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17182794.336000] end_request: I/O error, dev sda, sector 8
[17182794.336000] Buffer I/O error on device sda, logical block 1
[17182794.340000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17182794.340000] end_request: I/O error, dev sda, sector 16
[17182794.340000] Buffer I/O error on device sda, logical block 2
[17182794.344000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17182794.344000] end_request: I/O error, dev sda, sector 24
[17182794.344000] Buffer I/O error on device sda, logical block 3
[17182794.348000] sd 1:0:0:0: SCSI error: return code = 0x10070000
[17182794.348000] end_request: I/O error, dev sda, sector 0
[17182794.348000] Buffer I/O error on device sda, logical block 0

```

Anything else you guys need?

What should I do now?

---

### Post by jude999 on 2007-02-26
sorry... bump

---

