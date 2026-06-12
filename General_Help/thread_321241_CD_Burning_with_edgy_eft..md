---
title: "CD Burning with edgy eft."
date: 2006-12-18
forum: General Help
---

### Post by nip37 on 2006-12-18
Hello
i am having problem burning my CDs on ubuntu edgy eft. I had breezy and dapper before and i could burn CDs on both dist. On edgy eft when i insert blanck CD-R or CD-RW it does not bring dialouge to ask if i want to write disk or any options like it use to in dapper or in breezy, but still i can see CD-ROM Disk on desktop, i assume it does detect the disk.
when i try to burn files on that disk it keep asking me please insert a blank CD-R or CD-RW disk.i have tried 3 differnt brands of disks and i tried default CD/DVD burner application and also tried k3b and Brasero, but nothing seems to work.
below is output of cdrecord -prcap in terminal..
```
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'LG      '
Identifikation : 'CD-RW CED-8083B '
Revision       : '1.09'
Device seems to be: Generic mmc CD-RW.

Drive capabilities, per MMC page 2A:

  Does read CD-R media
  Does write CD-R media
  Does read CD-RW media
  Does write CD-RW media
  Does not read DVD-ROM media
  Does not read DVD-R media
  Does not write DVD-R media
  Does not read DVD-RAM media
  Does not write DVD-RAM media
  Does support test writing

  Does read Mode 2 Form 1 blocks
  Does read Mode 2 Form 2 blocks
  Does read digital audio blocks
  Does restart non-streamed digital audio reads accurately
  Does not support Buffer-Underrun-Free recording
  Does read multi-session CDs
  Does read fixed-packet CD media using Method 2
  Does not read CD bar code
  Does read R-W subcode information
  Does not return R-W subcode de-interleaved and error-corrected
  Does not read raw P-W subcode data from lead in
  Does return CD media catalog number
  Does return CD ISRC information
  Does not support C2 error pointers
  Does not deliver composite A/V data

  Does play audio CDs
  Number of volume control levels: 255
  Does support individual volume control setting for each channel
  Does support independent mute setting for each channel
  Does not support digital output on port 1
  Does not support digital output on port 2

  Loading mechanism type: tray
  Does support ejection of CD via START/STOP command
  Does not lock media on power up via prevent jumper
  Does allow media to be locked in the drive via PREVENT/ALLOW command
  Is not currently in a media-locked state
  Does not support changing side of disk
  Does not have load-empty-slot-in-changer feature
  Does not support Individual Disk Present feature

  Maximum read  speed:  5645 kB/s (CD  32x, DVD  4x)
  Current read  speed:   706 kB/s (CD   4x, DVD  0x)
  Maximum write speed:   706 kB/s (CD   4x, DVD  0x)
  Current write speed:   706 kB/s (CD   4x, DVD  0x)
  Buffer size in KB: 2048
```
any help will be appriciated, as i need to back up some data. Thanx

---

### Post by nip37 on 2006-12-19
any help !!! ??

---

### Post by kd7swh on 2006-12-19
Have you tried burning with K3B or Gnomebaker?

---

