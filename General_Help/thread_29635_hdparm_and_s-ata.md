---
title: "hdparm and s-ata"
date: 2005-04-25
forum: General Help
---

### Post by bts on 2005-04-25
hdparm seems not to be designed to work with S-ATA harddisks:

hdparm -y /dev/sda

/dev/sda:
 issuing standby command
 HDIO_DRIVE_CMD(standby) failed: Inappropriate ioctl for device

Is there a replacement included in hoary?

---

### Post by floogy on 2005-04-25
Hello,

I got the same Issue:

```
 lspci|grep ATA
0000:05:0a.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)

```
 hdparm -d1 /dev/sda
```
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24792/255/63, sectors = 203928109056, start = 0
```

but:
```
 hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

I found this, but without a hint of a replacement:
[http://ubuntuforums.org/archive/index.php/t-24046.html](http://ubuntuforums.org/archive/index.php/t-24046.html)

The only way seems to be to compile the kernel with the appropriate options.

Or try blktool. I'm wondering if it exists in any ubuntu repository for horay amd64.

[http://sourceforge.net/forum/forum.php?forum_id=399610](http://sourceforge.net/forum/forum.php?forum_id=399610)
[http://sourceforge.net/projects/gkernel/](http://sourceforge.net/projects/gkernel/)
[http://sourceforge.net/project/showfiles.php?group_id=3242&package_id=127086](http://sourceforge.net/project/showfiles.php?group_id=3242&package_id=127086)

> [http://packages.debian.org/unstable/admin/blktool](http://packages.debian.org/unstable/admin/blktool)

tune low-level block device parameters

blktool is used for querying and/or changing settings of a block device. It is like hdparm but a more general tool, as it works on SCSI, IDE and SATA devices.

This program is for those who know what they're doing and should be used it at your own risk as it could cause damage to your hardware. 

[http://ftp.ankara.edu.tr/debian-amd64/pool/main/b/blktool/](http://ftp.ankara.edu.tr/debian-amd64/pool/main/b/blktool/)

Yepp! It's in breezy, maybe it will be a good Idea to ask for a backport for horay i386 and amd64!
[http://packages.ubuntu.com/breezy/admin/blktool](http://packages.ubuntu.com/breezy/admin/blktool)

For me that doesn't work:

```
# dpkg -i blktool_4-2_amd64.deb
(Reading database ... 129306 files and directories currently installed.)
Preparing to replace blktool 4-2 (using blktool_4-2_amd64.deb) ...
Unpacking replacement blktool ...
dpkg: dependency problems prevent configuration of blktool:
 blktool depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing blktool (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 blktool
```
[COLOR=Green]
The debian package of blktool works for me![/COLOR]

But:
```
 blktool /dev/sda dma
HDIO_GET_DMA: Inappropriate ioctl for device
```

Setting the DMA for SATA Disk doesn't work at all... 

Anyway, I hope that helps.

regards

Gerhard

---

