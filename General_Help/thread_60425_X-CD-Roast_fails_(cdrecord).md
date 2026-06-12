---
title: "X-CD-Roast fails (cdrecord)"
date: 2005-08-27
forum: General Help
---

### Post by sinbad on 2005-08-27
Since the last kernel upgrade cdrecord fails in xcdroast when running it from my user account.
It worked fine before the upgrade. Running  
$sudo xcdroast
works fine. I have made sure that my user account is enabled to run xcdroast in the settings (confirmed when run as root). Seems like the last "upgrade" crapped out several apps.
Any help would be most appreciated.


Here is the error output:

Calling: /usr/lib/xcdroast/bin/xcdrwrap CDRECORD dev= "/dev/cdrom" gracetime=2 fs=16384k driveropts=burnfree -v -useinfo speed=24 -dao -eject -pad -overburn -audio "/home/jkl/shn/art2005-08-14d1t01.wav" ...

cdrecord: Warning: Running on Linux-2.6.10-5-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrom'
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
devname: '/dev/cdrom'
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
scsibus: -2 target: -2 lun: -2
and thus may have bugs that are not present in the original version.
Warning: Open by 'devname' is unintentional and not supported.
Please send bug reports and support requests to <cdrtools@packages.debian.org>.
Linux sg driver version: 3.5.27
The original author should not be bothered with problems of this version.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').

SCSI buffer size: 64512
TOC Type: 0 = CD-DA
cdrecord: Cannot allocate memory. Cannot get SCSI I/O buffer.
Using libscg version 'ubuntu-0.8ubuntu1'.

---

### Post by sinbad on 2005-08-29
Anybody?

---

