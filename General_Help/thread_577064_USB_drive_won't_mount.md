---
title: "USB drive won't mount"
date: 2007-10-15
forum: General Help
---

### Post by boltingaway on 2007-10-15
USB flash drive doesn't mount. Any help? 

Using Xubuntu version 7.04 Codename: Feisty Fawn

Output from mount -t vfat /dev/sdc /mnt/usbflash:

mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Output from fdisk -l:

Disk /dev/sdc: 4059 MB, 4059561984 bytes
229 heads, 32 sectors/track, 1081 cylinders
Units = cylinders of 7328 * 512 = 3751936 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?           1        1082     3964400    b  W95 FAT32

Output from dmesg:

[12438.600969] scsi 2:0:0:0: Direct-Access                               1100 PQ: 0 ANSI: 0 CCS
[12438.611910] SCSI device sdc: 7928832 512-byte hdwr sectors (4060 MB)
[12438.614929] sdc: Write Protect is off
[12438.614943] sdc: Mode Sense: 43 00 00 00
[12438.614948] sdc: assuming drive cache: write through
[12438.626918] SCSI device sdc: 7928832 512-byte hdwr sectors (4060 MB)
[12438.629898] sdc: Write Protect is off
[12438.629907] sdc: Mode Sense: 43 00 00 00
[12438.629911] sdc: assuming drive cache: write through
[12438.629920]  sdc: unknown partition table
[12438.712008] sd 2:0:0:0: Attached scsi removable disk sdc
[12438.712099] sd 2:0:0:0: Attached scsi generic sg4 type 0
[13284.847575] spurious 8259A interrupt: IRQ7.
[13608.024240] end_request: I/O error, dev fd0, sector 0
[13608.048234] end_request: I/O error, dev fd0, sector 0
[14368.313290] cramfs: wrong magic
........(says not ext3 and not ntfs) 
[15972.059589] FAT: invalid media value (0xb9)
[15972.059605] VFS: Can't find a valid FAT filesystem on dev sdc.

---

### Post by yabbadabbadont on 2007-10-15
It appears that the drive has a partition on it.
```
Device Boot Start End Blocks Id System
/dev/sdc1 ? 1 1082 3964400 b W95 FAT32
```
Try using /dev/sdc1 for the device in your command instead of /dev/sdc.

---

### Post by boltingaway on 2007-10-15
It says mount special device /dev/sdc1 does not exist.
Any other suggestions?

---

### Post by yabbadabbadont on 2007-10-15
Is there anything on the drive?  (that you want to keep that is)

---

### Post by boltingaway on 2007-10-15
yes.

---

### Post by yabbadabbadont on 2007-10-15
Can you still access the drive from Windows?  I'm assuming that you have Windows...  If so, try checking it for errors in Windows.

---

### Post by boltingaway on 2007-10-15
k, what should i do if it still doesnt work?

---

