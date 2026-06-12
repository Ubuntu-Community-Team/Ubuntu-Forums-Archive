---
title: "K3b burns dvd's but not cd's"
date: 2007-03-31
forum: General Help
---

### Post by element_G on 2007-03-31
K3b tells me i have a fifo error when I try to burn a cd, here's the debugging report:

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-11-386
Devices
-----------------------
HL-DT-ST DVDRAM GMA-4082N HV02 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 356138

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-11-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
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
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GMA-4082N'
Revision       : 'HV02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0015 
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
Drive DMA Speed: 13496 kB/s 76x CD 9x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data   695 MB        
Total size:      798 MB (79:08.50) = 356138 sectors
Lout start:      799 MB (79:10/38) = 356138 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 3708
Starting to write CD/DVD at speed 24 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.016s timeout 200s
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.016s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
Starting new track at sector: 0
Track 01:    0 of  695 MB written.
write track data: error after 0 bytes
Writing  time:   37.442s
Average write speed 127.1x.
Fixating...
Fixating time:    0.004s
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=24 -dao driveropts=burnfree -eject -data -tsize=356138s - 

mkisofs
-----------------------
356138
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.14% done, estimate finish Sat Mar 31 11:39:42 2007
  0.28% done, estimate finish Sat Mar 31 11:34:10 2007
  0.42% done, estimate finish Sat Mar 31 11:28:21 2007
  0.56% done, estimate finish Sat Mar 31 11:25:25 2007

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid house316hr -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-g-force/k3bkAXHDa.tmp -rational-rock -hide-list /tmp/kde-g-force/k3bh4UHub.tmp -joliet -hide-joliet-list /tmp/kde-g-force/k3btJuLfc.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-g-force/k3b2isgga.tmp 
</frame>

I'm on kubuntu 6.10 (edgy), I've tried SAO, TAO, and DAO, DMA is enabled, K3b will burn DVD's fine, have tried different files, turned off on the fly. The buffer meters always say "no info" except on TAO, they're at 100%, but still the same error. I've also tried gnomebaker, and I still get the error, and I've tried running K3b as su.

I hope I've provided enough information. Thanks;)

---

### Post by element_G on 2007-03-31
just bumping

---

### Post by element_G on 2007-03-31
bump

---

### Post by zvacet on 2007-04-01
[https://help.ubuntu.com/community/K3BHowto?highlight=%28k3b%29]("https://help.ubuntu.com/community/K3BHowto?highlight=%28k3b%29")

And mybe you will be interested in this
[http://k3b.plainblack.com/k3b-news/k3b-1.0-announcement]("http://k3b.plainblack.com/k3b-news/k3b-1.0-announcement")

---

### Post by element_G on 2007-04-01
Thanks! works like a charm :-D

---

