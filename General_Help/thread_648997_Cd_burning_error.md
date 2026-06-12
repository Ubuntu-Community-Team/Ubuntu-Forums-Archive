---
title: "Cd burning error"
date: 2007-12-24
forum: General Help
---

### Post by bfkeats on 2007-12-24
I recently switched to ubuntu, and I'm having trouble copying CD's. If I right-click and choose copy CD, I get the oh-so-useful message error writing cd. So I install k3b, and I get the error "Cdrecord has no permission to open the device" (Full error log below). I have done a "sudo chmod 777 /dev/hdc" which didn't help. Any ideas what's causing this?

```
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
Slimtype COMBO LSC-24082K JBK2 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'Slimtype'
Identification : 'COMBO LSC-24082K'
Revision       : 'JBK2'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1422080 = 1388 KB
FIFO size      : 12582912 = 12288 KB
Encoding speed : 464x (34768 sectors/s) for libedc from Heiko Eißfeldt
Speed set to 4234 KB/s
pregap1: -1
Track 01: audio  192 MB (19:04.80) no preemp     
Track 02: audio  242 MB (24:04.10) no preemp      pregapsize:   0
Total size:      435 MB (43:08.90) = 194168 sectors
Lout start:      435 MB (43:10/68) = 194168 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 165681
Forcespeed is OFF.
Starting to write CD/DVD at speed  24.0 in real RAW/RAW96R mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
/usr/bin/wodim: WARNING: Drive returns wrong startsec (0) using -11834 from ATIP
Writing lead-in at sector -11834
Lead-in write time:   26.311s
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  200 MB written.
Track 01:    1 of  200 MB written (fifo 100%) [buf  99%]  11.6x.
Track 01:    2 of  200 MB written (fifo 100%) [buf  99%]  11.2x.
Track 01:    3 of  200 MB written (fifo 100%) [buf  99%]  10.9x.
Track 01:    4 of  200 MB written (fifo 100%) [buf  99%]  11.3x.
Track 01:    5 of  200 MB written (fifo 100%) [buf  99%]  11.0x.
Track 01:    6 of  200 MB written (fifo 100%) [buf  99%]  11.4x.
Track 01:    7 of  200 MB written (fifo 100%) [buf  99%]  11.1x.
Track 01:    8 of  200 MB written (fifo 100%) [buf  99%]  11.5x.
Track 01:    9 of  200 MB written (fifo 100%) [buf  99%]  11.2x.
Track 01:   10 of  200 MB written (fifo 100%) [buf  99%]  11.6x.
Track 01:   11 of  200 MB written (fifo 100%) [buf  99%]  11.3x.
Track 01:   12 of  200 MB written (fifo 100%) [buf  99%]  11.7x.
Track 01:   13 of  200 MB written (fifo 100%) [buf  99%]  11.4x.
Track 01:   14 of  200 MB written (fifo 100%) [buf  99%]  11.8x.
Track 01:   15 of  200 MB written (fifo 100%) [buf  99%]  11.5x.
Track 01:   16 of  200 MB written (fifo 100%) [buf  99%]  11.9x.
Track 01:   17 of  200 MB written (fifo 100%) [buf  99%]  11.5x.
Track 01:   18 of  200 MB written (fifo 100%) [buf  99%]  12.0x.
Track 01:   19 of  200 MB written (fifo 100%) [buf  99%]  11.6x.
Track 01:   20 of  200 MB written (fifo 100%) [buf  99%]  12.0x.
Track 01:   21 of  200 MB written (fifo 100%) [buf  98%]  11.7x.
Track 01:   22 of  200 MB written (fifo 100%) [buf  99%]  11.5x.
Track 01:   23 of  200 MB written (fifo 100%) [buf  99%]  11.8x.
Track 01:   24 of  200 MB written (fifo 100%) [buf  99%]  11.5x.
Track 01:   25 of  200 MB written (fifo 100%) [buf  98%]  11.8x.
Track 01:   26 of  200 MB written (fifo 100%) [buf  99%]  11.7x.
Track 01:   27 of  200 MB written (fifo 100%) [buf  99%]  12.1x.
Track 01:   28 of  200 MB written (fifo 100%) [buf  99%]  11.7x.
Track 01:   29 of  200 MB written (fifo 100%) [buf  99%]  12.1x.
Track 01:   30 of  200 MB written (fifo  99%) [buf  99%]  11.8x.
Track 01:   31 of  200 MB written (fifo 100%) [buf  99%]  12.2x.
Track 01:   32 of  200 MB written (fifo 100%) [buf  99%]  11.9x.
Track 01:   33 of  200 MB written (fifo 100%) [buf  99%]  12.3x.
Track 01:   34 of  200 MB written (fifo 100%) [buf  99%]  12.0x.
Track 01:   35 of  200 MB written (fifo 100%) [buf  99%]  12.4x.
Track 01:   36 of  200 MB written (fifo 100%) [buf  99%]  12.1x.
Track 01:   37 of  200 MB written (fifo 100%) [buf  99%]  12.5x.
Track 01:   38 of  200 MB written (fifo 100%) [buf  98%]  12.1x.
Track 01:   39 of  200 MB written (fifo 100%) [buf  99%]  12.7x.
Track 01:   40 of  200 MB written (fifo 100%) [buf  99%]  12.2x.
Track 01:   41 of  200 MB written (fifo 100%) [buf  96%]  11.5x.
Track 01:   42 of  200 MB written (fifo 100%) [buf  99%]  12.9x.
Track 01:   43 of  200 MB written (fifo 100%) [buf  99%]  12.0x.
Track 01:   44 of  200 MB written (fifo 100%) [buf  98%]  12.4x.
Track 01:   45 of  200 MB written (fifo 100%) [buf  99%]  12.2x.
Track 01:   46 of  200 MB written (fifo 100%) [buf  97%]  12.2x.
Track 01:   47 of  200 MB written (fifo 100%) [buf  99%]  12.5x.
Track 01:   48 of  200 MB written (fifo 100%) [buf  99%]  12.6x.
Track 01:   49 of  200 MB written (fifo 100%) [buf  99%]  12.3x.
Track 01:   50 of  200 MB written (fifo  98%) [buf  98%]  12.5x.
Track 01:   51 of  200 MB written (fifo 100%) [buf  99%]  12.6x.
Track 01:   52 of  200 MB written (fifo 100%) [buf  99%]  12.8x.
Track 01:   53 of  200 MB written (fifo 100%) [buf  99%]  12.5x.
Track 01:   54 of  200 MB written (fifo 100%) [buf  99%]  12.9x.
Track 01:   55 of  200 MB written (fifo 100%) [buf  98%]  12.4x.
Track 01:   56 of  200 MB written (fifo 100%) [buf  99%]  13.1x.
Track 01:   57 of  200 MB written (fifo 100%) [buf  99%]  12.6x.
Track 01:   58 of  200 MB written (fifo 100%) [buf  99%]  13.1x.
Track 01:   59 of  200 MB written (fifo 100%) [buf  99%]  12.7x.
Track 01:   60 of  200 MB written (fifo 100%) [buf  99%]  13.2x.
Track 01:   61 of  200 MB written (fifo 100%) [buf  99%]   1.9x.
Track 01:   62 of  200 MB written (fifo 100%) [buf  99%]   8.0x.
Track 01:   63 of  200 MB written (fifo 100%) [buf  98%]   8.2x.
Track 01:   64 of  200 MB written (fifo 100%) [buf  99%]   8.1x.
Track 01:   65 of  200 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   66 of  200 MB written (fifo 100%) [buf  99%]   8.0x.
Track 01:   67 of  200 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   68 of  200 MB written (fifo 100%) [buf  99%]   8.1x.
Track 01:   69 of  200 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   70 of  200 MB written (fifo 100%) [buf  99%]   8.1x.
Track 01:   71 of  200 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   72 of  200 MB written (fifo 100%) [buf  99%]   8.1x.
Track 01:   73 of  200 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   74 of  200 MB written (fifo 100%) [buf  99%]   8.2x.
Track 01:   75 of  200 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   76 of  200 MB written (fifo 100%) [buf  99%]   8.2x.
Track 01:   77 of  200 MB written (fifo 100%) [buf  99%]   8.5x.
Track 01:   78 of  200 MB written (fifo 100%) [buf  99%]   8.2x.
Track 01:   79 of  200 MB written (fifo 100%) [buf  99%]   8.5x.
Track 01:   80 of  200 MB written (fifo 100%) [buf  99%]   8.2x.
Track 01:   81 of  200 MB written (fifo 100%) [buf  99%]   8.0x.
Track 01:   82 of  200 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   83 of  200 MB written (fifo 100%) [buf  99%]   8.0x.
Track 01:   84 of  200 MB written (fifo 100%) [buf  98%]   8.2x.
Track 01:   85 of  200 MB written (fifo 100%) [buf  98%]   8.0x.
Track 01:   86 of  200 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   87 of  200 MB written (fifo 100%) [buf  99%]   8.1x.
Track 01:   88 of  200 MB written (fifo 100%) [buf  99%]   8.4x.
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 94 2E 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63648
cmd finished after 5.999s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 92862432 bytes
Writing  time:   89.658s
Average write speed  40.9x.
Min drive buffer fill was 96%
Writing Leadout...
Fixating...
Fixating time:   29.541s
/usr/bin/wodim: fifo had 1651 puts and 1460 gets.
/usr/bin/wodim: fifo was 0 times empty and 1419 times full, min fill was 98%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/hdc speed=24 -raw96r driveropts=burnfree -eject -text -useinfo -audio -shorttrack /tmp/kde-bfkeats/k3bCdCopy0/Track01.wav /tmp/kde-bfkeats/k3bCdCopy0/Track02.wav 


```

---

### Post by SOULRiDER on 2007-12-24
What groups are you on? 
Type ```
groups
``` in a temrinal and post the output. I believe you need to be in optical to be able to burn things.

---

### Post by ajgreeny on 2007-12-24
I'm not in group **optical** and have never had a burning problem.  Is the CD copy protected?

---

### Post by SOULRiDER on 2007-12-24
Are you reading or writing from /dev/hdc? Its possible that it is copy protected, yes. Adding youself to the optical group cant hurt, why don you try it?

---

### Post by fishyf on 2007-12-24
I am having exactly the same problem on a Satelite Pro running gutsy. cdrecord -scanbus seems to indicate that my burner is
'MATSHITA' 'DVD-RAM UJ-842S '

I can burn DVDs without a problem using the default burner. I am pretty sure I could burn CDs in feisty.

---

