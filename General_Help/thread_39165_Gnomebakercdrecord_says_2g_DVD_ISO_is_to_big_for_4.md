---
title: "Gnomebaker/cdrecord says 2g DVD ISO is to big for 4.7g DVD-R!?"
date: 2005-06-03
forum: General Help
---

### Post by motionsiren on 2005-06-03
Im trying to burn a DVD ISO 2.7g big. I'm using Gnomebaker as the front end (nice job BTW, simple and fast workflow, keep it up!) and im using 4.7g rated media.

I select the ISO and click burn and then "viewing the output" of the "baking cd" dialog window, i reports:

```

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Found DVD media but DVD-R/DVD-RW support code is missing.
cdrecord: If you need DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
cdrecord: Free test versions and free keys for personal use are at ftp://ftp.berlios.de/pub/cdrecord/ProDVD/
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identifikation : 'DVDRW SOHW-1673S'
Revision       : 'JS02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 (current)
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 
Profile: 0x0008 
Using generic SCSI-3/mmc   CD/DVD driver (checks media) (mmc_cd_dvd).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1563904 = 1527 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Unspecified command not implemented for this drive.
cdrecord: Data will not fit on any disk.
cdrecord: Cannot write more than remaining DVD capacity.
Track 01: data  2701 MB        
Total size:     3101 MB (307:18.90) = 1382918 sectors
Lout start:     3102 MB (307:20/68) = 1382918 sectors
Current Secsize: 2048

```

any ideas why I cannot burn a 2.7g ISO onto a 4.7g media? im stumped. thanks!

---

### Post by arnieboy on 2005-06-04
try K3B. thats the closest that we can get to reliable DVD burning on linux.

---

### Post by motionsiren on 2005-11-28
Nah, k3B is no more reliable then the rest that are based on the same underlying applications.

K3B, AFAIK, is simply a GUI that brings it all together.
and does a greay job. but just like the others.

---

