---
title: "k3b problems"
date: 2006-10-26
forum: General Help
---

### Post by dannytherocker on 2006-10-26
Hi everybody, I've been using Edgy for 2 weeks and still have the same problem: k3b does not burn cd-rw with ext dvd recorder (don't know if it does cd-r with int cd recorder).
This is the k3b log:

[HTML]System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-386
Devices
-----------------------
QSI CDRW/DVD SBW242C UQ81 (/dev/hdc, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

PIODATA DVD-RW DVR-108DX 1.18 (/dev/scd0, /dev/sg0) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]
Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-10-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
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
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIODATA '
Identifikation : 'DVD-RW DVR-108DX'
Revision       : '1.18'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A (current)
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   698 MB        
Total size:      802 MB (79:27.81) = 357586 sectors
Lout start:      802 MB (79:29/61) = 357586 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 1
  Reference speed: 0
  Is not unrestricted
  Is erasable
  Disk sub type: Ultra High speed Rewritable media (2)
  ATIP start of lead in:  -11076 (97:34/24)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low: 16 1T speed high: 16
  2T speed low:  8 2T speed high: 24
  power mult factor: 4 5
  recommended erase/write power: 1
  A1 values: 66 4A 99
  A2 values: 38 80 00
  A3 values: 04 C4 A0
Disk type:    Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 2263
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
/usr/bin/X11/cdrecord: Cannot allocate memory. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1000 K BSize: 1000 K
Starting new track at sector: 0
Track 01:    0 of  698 MB written.
/usr/bin/X11/cdrecord: Cannot allocate memory. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   17.701s
Average write speed 949.3x.
Fixating...
Fixating time:    0.013s
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=0,0,0 speed=24 -dao driveropts=burnfree -eject -data /media/USB50/software/Linux-Images/Ubuntu/Dapper 6.06/ubuntu-6.06.1-desktop-i386.iso 

[/HTML]

How can I fix?
thanks in advance

---

### Post by taurus on 2006-10-26
Have you tried with other burning programs like gnomebaker, xcdroast, or even nautilus?

---

### Post by Osamabingandhi on 2006-10-27
I have tried gnomebaker and that doesn't work either. Is there a way to fix k3b or gnomebaker to be able to burn? The only program that has worked for me is by using dvddecryptor through wine....I would prefer to use a linux program :-)

---

### Post by dannytherocker on 2006-10-28
> **Osamabingandhi said:**
> I have tried gnomebaker and that doesn't work either. Is there a way to fix k3b or gnomebaker to be able to burn? The only program that has worked for me is by using dvddecryptor through wine....I would prefer to use a linux program :-)

Gnomebaker doesn't work on my pc, as well!!! the only way is the command line! I was able to burn a cd by typing cdrecord...etc...etc..
I don't know why!

---

