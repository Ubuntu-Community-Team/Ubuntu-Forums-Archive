---
title: "Recover data from CompactFlash drive"
date: 2007-06-09
forum: General Help
---

### Post by adam.skinner on 2007-06-09
So I have an old Rio Carbon that has some music on it that I don't have anywhere else.  I'd like to recover the data from it, only the Carbon was displaying an "Upgrader" message and was essentially borked.  Long story short, I removed the 5G CF drive from it, stuck it in a USB card reader, and expected it to work.  D'oh!  t fdisk -l is saying that "Disk /dev/sdb doesn't contain a valid partition table".

What are my options?  Can I do a raw data copy from sdb to a file and then work with that file?

dmesg:
```

[  283.233960] usb 1-4: USB disconnect, address 3
[  286.540009] usb 1-4: new high speed USB device using ehci_hcd and address 4
[  286.691282] usb 1-4: configuration #1 chosen from 1 choice
[  286.691517] scsi9 : SCSI emulation for USB Mass Storage devices
[  286.691632] usb-storage: device found at 4
[  286.691634] usb-storage: waiting for device to settle before scanning
[  291.689186] usb-storage: device scan complete
[  291.693312] scsi 9:0:0:0: Direct-Access     GENERIC  USB Storage-CFC  I16B PQ: 0 ANSI: 0 CCS
[  291.697303] scsi 9:0:0:1: Direct-Access     GENERIC  USB Storage-MSC  I16B PQ: 0 ANSI: 0 CCS
[  291.701302] scsi 9:0:0:2: Direct-Access     GENERIC  USB Storage-SMC  I16B PQ: 0 ANSI: 0 CCS
[  291.705297] scsi 9:0:0:3: Direct-Access     GENERIC  USB Storage-SDC  I16B PQ: 0 ANSI: 0 CCS
[  291.708908] SCSI device sdb: 9767520 512-byte hdwr sectors (5001 MB)
[  291.709532] sdb: Write Protect is off
[  291.709537] sdb: Mode Sense: 03 00 00 00
[  291.709541] sdb: assuming drive cache: write through
[  291.713154] SCSI device sdb: 9767520 512-byte hdwr sectors (5001 MB)
[  291.713779] sdb: Write Protect is off
[  291.713783] sdb: Mode Sense: 03 00 00 00
[  291.713786] sdb: assuming drive cache: write through
[  291.713789]  sdb: unknown partition table
[  293.997956] sd 9:0:0:0: Attached scsi removable disk sdb
[  293.998004] sd 9:0:0:0: Attached scsi generic sg2 type 0
[  293.999183] sd 9:0:0:1: Attached scsi removable disk sdc
[  293.999225] sd 9:0:0:1: Attached scsi generic sg3 type 0
[  294.000489] sd 9:0:0:2: Attached scsi removable disk sdd
[  294.000536] sd 9:0:0:2: Attached scsi generic sg4 type 0
[  294.003698] sd 9:0:0:3: Attached scsi removable disk sde
[  294.003747] sd 9:0:0:3: Attached scsi generic sg5 type 0

```

fdisk -l
```
Disk /dev/sdb: 5000 MB, 5000970240 bytes
154 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 9548 * 512 = 4888576 bytes

Disk /dev/sdb doesn't contain a valid partition table
```

---

### Post by tgalati4 on 2007-06-09
Sounds like the update borked the partition table, taking your music with it.  These are normally formatted with FAT32.  Perhaps you can hang it off of a windows machine and use Norton Utilities to perform a data recovery using Disk Doctor.  Let us know if you have any luck.

---

### Post by trippinnik on 2007-06-09
there's a few free way to do that linux too.  one is to use partimage and make an image from the disk and then you can mount that and fsck it.  you can also try photorec, while meant for pics i think it can be used for other files too, I was able to retrieve almost all of my friends files when she deleted them from the card and even began using the card again.

---

### Post by adam.skinner on 2007-06-09
> **trippinnik said:**
> there's a few free way to do that linux too.  one is to use partimage and make an image from the disk and then you can mount that and fsck it.  you can also try photorec, while meant for pics i think it can be used for other files too, I was able to retrieve almost all of my friends files when she deleted them from the card and even began using the card again.

Totally awesome!  Firstly, partimage wasn't able to see my partition; in fact, it didn't even recognise a partition on the drive, so that was a bust.

Then I tried to use testdisk, and that failed.  But I found photorec on the same site (now I understand why it came up in apt-cache search) and that was actually able to recover my files!

Sweet!

Thanks!  Now all I need to do is retag my mp3s =) hehe

---

### Post by punong_bisyonaryo on 2007-06-11
I also get a ¨Disk /dev/sda doesn't contain a valid partition table¨.  And when I run ¨sudo fsck.vfat /dev/sda¨ I get:
```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 41.
```

I also tried testdisk and I get a ¨Partition sector doesn't have the endmark 0xAA55¨. After it runs its analyses, it doesn´t fix anything, it just gives me a list of 0 partitions and options to add partitions.

I also used gddrescue and backed up the image to a file, is this the same as partimage?

I would try photorec, but the contents of the drive are important .sav files, so i´m not sure if it would work. photorec is also not in my repositories...:(

help:-?

---

