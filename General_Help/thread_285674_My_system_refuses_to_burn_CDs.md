---
title: "My system refuses to burn CDs"
date: 2006-10-27
forum: General Help
---

### Post by Amurko on 2006-10-27
My system burns DVDs fine..  but for some reason, it stubburnly refuses to burn CDs.  This problem was around ever since I started with Dapper and upgrading to Edgy did nothing to resolve it (not that I was expecting it to.)

What I've tried:

burning in Gnomebaker (failed)
burning in K3b (failed)
burning using the command line (failed, although I didn't try too many combinations of parameters)

Burning with the above three schemes using sudo (failed 3x)

here's my Gnomebaker error output:

> cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'TOSHIBA '
Identifikation : 'DVD-ROM SD-R5002'
Revision       : '1033'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x0010 
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A (current)
Profile: 0x0011 
Profile: 0x0013 
Profile: 0x0014 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1723392 = 1683 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Probably trying to use ultra high speed medium on improper writer.
cdrecord: fifo had 6 puts and 0 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 0%.


And here's my K3b error output:

> 
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-generic
Devices
-----------------------
TOSHIBA DVD-ROM SD-R5002 1033 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R96R; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 185

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/X11R6/bin/cdrecord: Warning: Running on Linux-2.6.17-10-generic
/usr/X11R6/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/X11R6/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/X11R6/bin/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/X11R6/bin/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/X11R6/bin/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'TOSHIBA '
Identifikation : 'DVD-ROM SD-R5002'
Revision       : '1033'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x0010 
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A (current)
Profile: 0x0011 
Profile: 0x0013 
Profile: 0x0014 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1723392 = 1683 KB
FIFO size      : 4194304 = 4096 KB
/usr/X11R6/bin/cdrecord: Probably trying to use ultra high speed medium on improper writer.
/usr/X11R6/bin/cdrecord: fifo had 6 puts and 0 gets.
/usr/X11R6/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 0%.
Track 01: data     0 MB         padsize:  230 KB
Total size:        0 MB (00:04.02) = 302 sectors
Lout start:        1 MB (00:06/02) = 302 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Reference speed: 0
  Is not unrestricted
  Is erasable
  Disk sub type: Ultra High speed Rewritable media (2)
  ATIP start of lead in:  -11744 (97:25/31)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Phase change
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 359546

cdrecord command:
-----------------------
/usr/X11R6/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=16 -tao driveropts=burnfree -eject -multi -xa -tsize=185s - 

mkisofs
-----------------------
185
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
Total translation table size: 0
Total rockridge attributes bytes: 263
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 0
185 extents written (0 MB)

mkisofs command:
-----------------------
/usr/X11R6/bin/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-root/k3bphVuqc.tmp -rational-rock -hide-list /tmp/kde-root/k3bEic3ga.tmp -joliet -hide-joliet-list /tmp/kde-root/k3bfzVOFa.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-root/k3bBwgOUb.tmp 


I think the key to the error is:

> 
/usr/X11R6/bin/cdrecord: Probably trying to use ultra high speed medium on improper writer.



What else is there to try besides getting a new DVD recorder or downgrading to the 2.4 kernel (as suggested)?  Btw, this system burned CDs and DVDs fine when I used to use XP.

---

