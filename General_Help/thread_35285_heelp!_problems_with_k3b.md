---
title: "heelp! problems with k3b"
date: 2005-05-18
forum: General Help
---

### Post by hrvoje-pula on 2005-05-18
i'm haveing problems with k3b. everything seem to be fine but then ont the third song it stops and is written : error code 254.

it can only burn 2 songs
this is debug report:

Devices
-----------------------
_NEC DVD_RW ND-3500AG 2.16 (/dev/hdc, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; RAW/R96R]
TSSTcorp DVD-ROM TS-H352A TS01 (/dev/hda, ) at /media/cdrom0 [CD-ROM; DVD-ROM; DVD+R] [DVD-ROM; DVD+R Double Layer; CD-ROM] [None]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-k7

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.10-5-k7
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : '_NEC    '
Identifikation : 'DVD_RW ND-3500AG'
Revision       : '2.16'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 1343488 = 1312 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   22 MB (02:12.49) no preemp copy
Track 02: audio   34 MB (03:27.96) no preemp copy
Track 03: audio   16 MB (01:37.98) no preemp copy
Track 04: audio   15 MB (01:32.18) no preemp copy
Track 05: audio   31 MB (03:07.81) no preemp copy
Track 06: audio   17 MB (01:42.89) no preemp copy
Track 07: audio   19 MB (01:55.88) no preemp copy
Track 08: audio   15 MB (01:29.72) no preemp copy
Track 09: audio   15 MB (01:30.37) no preemp copy
Track 10: audio   21 MB (02:07.36) no preemp copy
Total size:      209 MB (20:44.66) = 93350 sectors
Lout start:      209 MB (20:46/50) = 93350 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type C, low Beta category (C-) (6)
  ATIP start of lead in:  -11231 (97:32/19)
  ATIP start of lead out: 359847 (79:59/72)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 27
Manufacturer: Prodisc Technology Inc.
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
Blocks total: 359847 Blocks current: 359847 Blocks remaining: 266497
Starting to write CD/DVD at speed 32 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
SAO startsec: -11231
Writing lead-in...
Lead-in write time:   20.930s
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   22 MB written.
Track 01:    1 of   22 MB written (fifo 100%) [buf  60%]  12.5x.
Track 01:    2 of   22 MB written (fifo 100%) [buf  26%]  12.5x.
Track 01:    3 of   22 MB written (fifo 100%) [buf  15%]  12.9x.
Track 01:    4 of   22 MB written (fifo 100%) [buf  85%]  12.3x.
Track 01:    5 of   22 MB written (fifo 100%) [buf  80%]   5.6x.
Track 01:    6 of   22 MB written (fifo 100%) [buf  42%]  12.2x.
Track 01:    7 of   22 MB written (fifo 100%) [buf   8%]  12.8x.
Track 01:    8 of   22 MB written (fifo 100%) [buf  58%]  11.9x.
Track 01:    9 of   22 MB written (fifo 100%) [buf  92%]   5.6x.
Track 01:   10 of   22 MB written (fifo 100%) [buf  54%]  12.2x.
Track 01:   11 of   22 MB written (fifo 100%) [buf  19%]  12.7x.
Track 01:   12 of   22 MB written (fifo 100%) [buf  37%]  12.4x.
Track 01:   13 of   22 MB written (fifo 100%) [buf 100%]  11.8x.
Track 01:   14 of   22 MB written (fifo 100%) [buf  67%]   5.9x.
Track 01:   15 of   22 MB written (fifo 100%) [buf  32%]  12.7x.
Track 01:   16 of   22 MB written (fifo 100%) [buf  12%]  12.1x.
Track 01:   17 of   22 MB written (fifo 100%) [buf  78%]  12.6x.
Track 01:   18 of   22 MB written (fifo 100%) [buf  79%]   5.7x.
Track 01:   19 of   22 MB written (fifo 100%) [buf  42%]  12.7x.
Track 01:   20 of   22 MB written (fifo 100%) [buf   3%]  12.3x.
Track 01:   21 of   22 MB written (fifo 100%) [buf  66%]  12.5x.
Track 01:   22 of   22 MB written (fifo 100%) [buf  84%]   5.6x.
Track 01: Total bytes read/written: 23371824/23371824 (9937 sectors).
Starting new track at sector: 9937
Track 02:    0 of   34 MB written.
Track 02:    1 of   34 MB written (fifo 100%) [buf  34%]  12.5x.
Track 02:    2 of   34 MB written (fifo 100%) [buf  13%]  12.2x.
Track 02:    3 of   34 MB written (fifo 100%) [buf  79%]  12.6x.
Track 02:    4 of   34 MB written (fifo 100%) [buf  77%]   5.8x.
Track 02:    5 of   34 MB written (fifo 100%) [buf  39%]  12.8x.
Track 02:    6 of   34 MB written (fifo 100%) [buf   7%]  12.4x.
Track 02:    7 of   34 MB written (fifo 100%) [buf  73%]  12.6x.
Track 02:    8 of   34 MB written (fifo 100%) [buf  80%]   5.8x.
Track 02:    9 of   34 MB written (fifo 100%) [buf  38%]  12.5x.
Track 02:   10 of   34 MB written (fifo 100%) [buf   7%]  12.3x.
Track 02:   11 of   34 MB written (fifo 100%) [buf  73%]  12.6x.
Track 02:   12 of   34 MB written (fifo 100%) [buf  79%]   5.8x.
Track 02:   13 of   34 MB written (fifo 100%) [buf  38%]  12.8x.
Track 02:   14 of   34 MB written (fifo 100%) [buf  10%]  12.2x.
Track 02:   15 of   34 MB written (fifo 100%) [buf  76%]  12.6x.
Track 02:   16 of   34 MB written (fifo 100%) [buf  77%]   5.9x.
Track 02:   17 of   34 MB written (fifo 100%) [buf  34%]  12.6x.
Track 02:   18 of   34 MB written (fifo 100%) [buf  19%]  11.9x.
Track 02:   19 of   34 MB written (fifo 100%) [buf  84%]  10.8x.
Track 02:   20 of   34 MB written (fifo 100%) [buf  60%]  12.3x.
Track 02:   21 of   34 MB written (fifo 100%) [buf  17%]  12.7x.
Track 02:   22 of   34 MB written (fifo 100%) [buf  47%]  12.3x.
Track 02:   23 of   34 MB written (fifo 100%) [buf  99%]  10.0x.
Track 02:   24 of   34 MB written (fifo 100%) [buf  77%]  12.4x.
Track 02:   25 of   34 MB written (fifo 100%) [buf  55%]  12.6x.
Track 02:   26 of   34 MB written (fifo 100%) [buf  34%]  12.4x.
Track 02:   27 of   34 MB written (fifo 100%) [buf  14%]  12.7x.
Track 02:   28 of   34 MB written (fifo 100%) [buf  29%]  12.3x.
Track 02:   29 of   34 MB written (fifo 100%) [buf  95%]  12.1x.
Track 02:   30 of   34 MB written (fifo 100%) [buf  85%]  10.1x.
Track 02:   31 of   34 MB written (fifo 100%) [buf  65%]  12.7x.
Track 02:   32 of   34 MB written (fifo 100%) [buf  43%]  12.4x.
Track 02:   33 of   34 MB written (fifo 100%) [buf  22%]  12.5x.
Track 02:   34 of   34 MB written (fifo 100%) [buf   1%]  12.3x.
Track 02: Total bytes read/written: 36684144/36684144 (15597 sectors).
Starting new track at sector: 25534
Track 03:    0 of   16 MB written.
/usr/bin/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 64 B1 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 62 16 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 25110 (not valid) 
resid: 25872
cmd finished after 23.501s timeout 200s
/usr/bin/cdrecord: A write error occured.
/usr/bin/cdrecord: Please properly read the error message above.
write track data: error after 571536 bytes
Writing  time:   83.681s
Average write speed  19.8x.
Min drive buffer fill was 1%
Total of 2 possible drive buffer underruns predicted.
Fixating...
Fixating time:    0.001s
/usr/bin/cdrecord: fifo had 1020 puts and 957 gets.
BURN-Free was 12 times used.
/usr/bin/cdrecord: fifo was 0 times empty and 955 times full, min fill was 96%.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=32 -dao driveropts=burnfree -eject -useinfo -text -pad -shorttrack -audio /tmp/kde-hrvoje/k3b_audio_0_01.wav /tmp/kde-hrvoje/k3b_audio_0_02.wav /tmp/kde-hrvoje/k3b_audio_0_03.wav /tmp/kde-hrvoje/k3b_audio_0_04.wav /tmp/kde-hrvoje/k3b_audio_0_05.wav /tmp/kde-hrvoje/k3b_audio_0_06.wav /tmp/kde-hrvoje/k3b_audio_0_07.wav /tmp/kde-hrvoje/k3b_audio_0_08.wav /tmp/kde-hrvoje/k3b_audio_0_09.wav /tmp/kde-hrvoje/k3b_audio_0_10.wav 


does anybody know what to do?

---

### Post by Ferio on 2005-10-23
I'm having problems with K3b, and with GNOMEBaker, GCombust, Graveman,  Nautilus, NeroLINUX... I was able to burn media while I used 5.04, but after updating to 5.10, I only got to burn one double layer DVD, and that was that. It has broken 8 DD-DVDs yet :S

---

### Post by wobster on 2005-10-29
So funny. Look what cdrecord says:

[13:48:38] wobster@xxxxxx ~ $ cdrecord --version
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.




Which moron added this?!

---

