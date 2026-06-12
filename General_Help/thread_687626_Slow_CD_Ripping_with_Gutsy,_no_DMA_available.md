---
title: "Slow CD Ripping with Gutsy, no DMA available"
date: 2008-02-04
forum: General Help
---

### Post by phen on 2008-02-04
Hello!

I am using a Thinkpad X31, and the CD drive is in the docking station. My harddisk and my Cdrom are /dev/sda and sdb and it is not possible to turn on DMA.


```
kai@schlepptop:~$ sudo hdparm -d 1 /dev/sdb

/dev/sdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument

```

Its not a scsi drive, Ripping is slow to impossible with speeds of 0,0x to 0,2x. Listening to CDs is ok, and it is possible to watch DVDs without problems.

I tried to turn of autoplay and paranoia with sound juicer and grip. no effect :confused:


thanks for your help!

---

