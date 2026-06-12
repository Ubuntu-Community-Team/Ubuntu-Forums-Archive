---
title: "I can burn only with nautilus???"
date: 2006-12-16
forum: General Help
---

### Post by ghosthead123 on 2006-12-16
On my brand new pc P4 with LG DVD/CD writer i cant burn cd's . The onlyest program that works  
is nautilus???? I try xcdroast, k3b and gnomebaker. I try to fix the permisions DMA and other stuff but it did not help. 
I thing that the problem is in hardware driver for LG but I am not sure.
That's my k3b log:
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-H10N JL10 (/dev/scd0, /dev/sg2) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

K3b
-----------------------
Size of filesystem calculated: 135545

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-10-generic
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,1,0'
scsibus: 1 target: 1 lun: 0
Linux sg driver version: 3.5.33
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
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
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-H10N '
Revision       : 'JL10'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0015 
Profile: 0x0016 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 14147 kB/s 80x CD 10x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data   264 MB        
Total size:      304 MB (30:07.29) = 135547 sectors
Lout start:      304 MB (30:09/22) = 135547 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 7
  Is not unrestricted
  Is not erasable
  ATIP start of lead in:  -11597 (97:27/28)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 20
Manufacturer: Princo Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 224302
Starting to write CD/DVD at speed 48 in real TAO mode for multi session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  264 MB written.
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 01 36 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.016s timeout 40s
/usr/bin/X11/cdrecord: The current problem looks like a buffer underrun.
/usr/bin/X11/cdrecord: It looks like 'driveropts=burnfree' does not work for this drive.
/usr/bin/X11/cdrecord: Please report.
/usr/bin/X11/cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.
write track data: error after 634880 bytes
Writing  time:   13.735s
Average write speed 132.5x.
Fixating...
Fixating time:   17.517s
/usr/bin/X11/cdrecord: fifo had 74 puts and 11 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 1 times full, min fill was 87%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,1,0 speed=48 -tao driveropts=burnfree -eject -multi -xa -tsize=135545s - 

mkisofs
-----------------------
135545
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.

Using sergei_snurov___bumer_2_000.mp3;1 for  bumer2/2/sergei snurov - bumer 2 - svoboda.mp3 (sergei snurov - bumer 2 - skorost.mp3)
Using sergei_snurov___bumer_2_001.mp3;1 for  bumer2/2/sergei snurov - bumer 2 - skorost.mp3 (sergei snurov - bumer 2 - skorost ( denisbee speed edit).mp3)
  0.38% done, estimate finish Sat Dec 16 14:21:52 2006
  0.74% done, estimate finish Sat Dec 16 14:17:29 2006
  1.11% done, estimate finish Sat Dec 16 14:16:00 2006
  1.49% done, estimate finish Sat Dec 16 14:15:14 2006
/usr/bin/X11/mkisofs: Connection reset by peer. cannot fwrite 32768*1

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-ivan/k3bV1Q1fc.tmp -rational-rock -hide-list /tmp/kde-ivan/k3bOTBoba.tmp -joliet -hide-joliet-list /tmp/kde-ivan/k3bLH0bXb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-ivan/k3bjRKsPb.tmp 


/I'm sorry for my bad english, i'm from Bulgaria/

---

### Post by nyarla33 on 2007-01-06
I have the same issue here (Ubuntu 6.10).
I have tried K3b, Brasero and Graveman.

Burning with Nautilus has this issue:
[https://launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/67034](https://launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/67034)
But the CD/DVD seem to be burnt correctly though.

More details if needed.

---

