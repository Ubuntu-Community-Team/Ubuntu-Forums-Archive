---
title: "Cd burning completes, but disk is empty"
date: 2006-12-15
forum: General Help
---

### Post by Eddy Dean on 2006-12-15
Hello,

Today I tried to burn an ISO image to an CD. Everything worked, without any errors and warnings, but the disk is still empty. I've tried K3B and the command-line cdrecord to burn, and both give no errors, take some time, and the CD burner even gets busy, but nothing gets written to the CD. Yesterday I did exactly the same, but then it did work. The MD5 Sum is correct, so I can't imagine the ISO being empty.

Greetz,
Arno

---

### Post by ZERO_SHIFT on 2006-12-15
I think what you did is burn the image on the CD. You should turn the image----->to a-----> CD. You can do that by right-mouse-clicking on the .iso image and then choosing the -burn to disc- option.

---

### Post by Eddy Dean on 2006-12-15
Thanks, but I've done that too. And even if I wrote the iso file to the disk instead of the image, the disk wouldn't show up as empty then...

---

### Post by _simon_ on 2006-12-15
Bad disc or problem with your drive

I've never had any issues with k3b when burning CD's or DVD's.

Try gnomebaker, if you still have the same issue I'd be thinking the drive was faulty.

---

### Post by Eddy Dean on 2006-12-15
Not working. It's burning the CD, but the disk remains empty. I've tried several blank CDs and none of them worked. Is there any way to test the drive? (except for trying to burn?)

The gnome-baker output:
```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-27-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ARTEC   '
Identifikation : 'WRR-4848        '
Revision       : '1.00'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x0008 
Profile: 0x0009 (current)
Profile: 0x000A 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1359872 = 1328 KB
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
Starting new track at sector: 0
Writing  time:  508.613s
Average write speed   8.0x.
Min drive buffer fill was 94%
Fixating...
Fixating time:   35.097s
cdrecord: fifo had 9752 puts and 9752 gets.
cdrecord: fifo was 0 times empty and 9603 times full, min fill was 79%.
```

---

