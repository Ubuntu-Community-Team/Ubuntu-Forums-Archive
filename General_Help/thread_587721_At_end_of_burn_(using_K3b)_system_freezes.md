---
title: "At end of burn (using K3b) system freezes"
date: 2007-10-23
forum: General Help
---

### Post by bitterbug on 2007-10-23
So I've done a fresh install with 7.10 and unfortunately my k3b crash won't go away.
As soon as it completes a disc the system hangs, and even SysRq+REISUB has no effect.

The burned discs turn out fine, but I don't think it's worth the possible data corruption on the hard drive :(

Here's a copy of the logs from a simulation run. Interestingly it gives a write error at the end of the sim.

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
HL-DT-ST DVD-RAM GSA-H54N 1.00 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 8.2x1352KBps.
   26476544/3631452160 ( 0.7%) @4.0x, remaining 13:36 RBU 100.0% UBU   7.0%
   45088768/3631452160 ( 1.2%) @4.0x, remaining 11:55 RBU 100.0% UBU  83.9%
   63569920/3631452160 ( 1.8%) @4.0x, remaining 12:09 RBU 100.0% UBU  83.9%
   82182144/3631452160 ( 2.3%) @4.0x, remaining 11:31 RBU 100.0% UBU  83.9%
  100728832/3631452160 ( 2.8%) @4.0x, remaining 11:05 RBU 100.0% UBU  83.9%
  119275520/3631452160 ( 3.3%) @4.0x, remaining 11:17 RBU 100.0% UBU  83.9%
  137887744/3631452160 ( 3.8%) @4.0x, remaining 10:58 RBU 100.0% UBU  83.9%
  156368896/3631452160 ( 4.3%) @4.0x, remaining 10:44 RBU 100.0% UBU  83.9%
  174981120/3631452160 ( 4.8%) @4.0x, remaining 10:51 RBU 100.0% UBU  83.9%
  193560576/3631452160 ( 5.3%) @4.0x, remaining 10:39 RBU 100.0% UBU  83.9%
  212074496/3631452160 ( 5.8%) @4.0x, remaining 10:28 RBU 100.0% UBU  83.9%
  230686720/3631452160 ( 6.4%) @4.0x, remaining 10:33 RBU 100.0% UBU  83.9%
  249167872/3631452160 ( 6.9%) @4.0x, remaining 10:24 RBU 100.0% UBU  83.9%
  267780096/3631452160 ( 7.4%) @4.0x, remaining 10:15 RBU 100.0% UBU  83.9%
  286261248/3631452160 ( 7.9%) @4.0x, remaining 10:19 RBU 100.0% UBU  83.9%
  304873472/3631452160 ( 8.4%) @4.0x, remaining 10:11 RBU 100.0% UBU  83.9%
  323485696/3631452160 ( 8.9%) @4.0x, remaining 10:03 RBU 100.0% UBU  83.9%
  341966848/3631452160 ( 9.4%) @4.0x, remaining 10:06 RBU 100.0% UBU  83.9%
  360579072/3631452160 ( 9.9%) @4.0x, remaining 9:58 RBU 100.0% UBU  83.9%
  379092992/3631452160 (10.4%) @4.0x, remaining 9:51 RBU 100.0% UBU  83.9%
  397672448/3631452160 (11.0%) @4.0x, remaining 9:53 RBU 100.0% UBU  83.9%
  416284672/3631452160 (11.5%) @4.0x, remaining 9:46 RBU 100.0% UBU  83.9%
  434765824/3631452160 (12.0%) @4.0x, remaining 9:40 RBU 100.0% UBU  83.9%
  453378048/3631452160 (12.5%) @4.0x, remaining 9:41 RBU 100.0% UBU  83.9%
  471859200/3631452160 (13.0%) @4.0x, remaining 9:35 RBU 100.0% UBU  83.9%
  490471424/3631452160 (13.5%) @4.0x, remaining 9:29 RBU 100.0% UBU  83.9%
  504791040/3631452160 (13.9%) @3.1x, remaining 9:36 RBU 100.0% UBU  83.9%
  521306112/3631452160 (14.4%) @3.6x, remaining 9:32 RBU 100.0% UBU  90.8%
  539787264/3631452160 (14.9%) @4.0x, remaining 9:32 RBU 100.0% UBU  90.8%
  558399488/3631452160 (15.4%) @4.0x, remaining 9:26 RBU 100.0% UBU  90.8%
  577011712/3631452160 (15.9%) @4.0x, remaining 9:21 RBU 100.0% UBU  90.8%
  595492864/3631452160 (16.4%) @4.0x, remaining 9:20 RBU 100.0% UBU  90.8%
  614105088/3631452160 (16.9%) @4.0x, remaining 9:15 RBU 100.0% UBU  90.8%
  632619008/3631452160 (17.4%) @4.0x, remaining 9:09 RBU 100.0% UBU  90.8%
  651198464/3631452160 (17.9%) @4.0x, remaining 9:09 RBU 100.0% UBU  90.8%
  669810688/3631452160 (18.4%) @4.0x, remaining 9:03 RBU 100.0% UBU  90.8%
  672497664/3631452160 (18.5%) @0.6x, remaining 9:14 RBU 100.0% UBU  90.8%
  690061312/3631452160 (19.0%) @3.8x, remaining 9:14 RBU 100.0% UBU  86.2%
  727154688/3631452160 (20.0%) @8.0x, remaining 8:51 RBU 100.0% UBU  86.2%
  764248064/3631452160 (21.0%) @8.0x, remaining 8:30 RBU 100.0% UBU  86.2%
  801341440/3631452160 (22.1%) @8.0x, remaining 8:14 RBU 100.0% UBU  86.2%
  838500352/3631452160 (23.1%) @8.0x, remaining 7:56 RBU 100.0% UBU  86.2%
  875626496/3631452160 (24.1%) @8.0x, remaining 7:39 RBU 100.0% UBU  86.2%
  912752640/3631452160 (25.1%) @8.0x, remaining 7:26 RBU 100.0% UBU  86.2%
  949846016/3631452160 (26.2%) @8.0x, remaining 7:11 RBU 100.0% UBU  86.2%
  986939392/3631452160 (27.2%) @8.0x, remaining 6:58 RBU 100.0% UBU  86.2%
 1024032768/3631452160 (28.2%) @8.0x, remaining 6:47 RBU 100.0% UBU  86.2%
 1061191680/3631452160 (29.2%) @8.0x, remaining 6:34 RBU 100.0% UBU  86.2%
 1092091904/3631452160 (30.1%) @6.7x, remaining 6:25 RBU 100.0% UBU  86.2%
 1129185280/3631452160 (31.1%) @8.0x, remaining 6:16 RBU 100.0% UBU  88.5%
 1166344192/3631452160 (32.1%) @8.0x, remaining 6:05 RBU 100.0% UBU  88.5%
 1203437568/3631452160 (33.1%) @8.0x, remaining 5:55 RBU 100.0% UBU  88.5%
 1240563712/3631452160 (34.2%) @8.0x, remaining 5:46 RBU 100.0% UBU  88.5%
 1277689856/3631452160 (35.2%) @8.0x, remaining 5:37 RBU 100.0% UBU  88.5%
 1314848768/3631452160 (36.2%) @8.0x, remaining 5:27 RBU 100.0% UBU  88.5%
 1351942144/3631452160 (37.2%) @8.0x, remaining 5:20 RBU 100.0% UBU  88.5%
 1389035520/3631452160 (38.3%) @8.0x, remaining 5:11 RBU 100.0% UBU  88.5%
 1426128896/3631452160 (39.3%) @8.0x, remaining 5:03 RBU 100.0% UBU  88.5%
 1463222272/3631452160 (40.3%) @8.0x, remaining 4:56 RBU 100.0% UBU  88.5%
 1493958656/3631452160 (41.1%) @6.6x, remaining 4:50 RBU 100.0% UBU  83.9%
 1531052032/3631452160 (42.2%) @8.0x, remaining 4:42 RBU 100.0% UBU  83.9%
 1568145408/3631452160 (43.2%) @8.0x, remaining 4:36 RBU 100.0% UBU  83.9%
 1605271552/3631452160 (44.2%) @8.0x, remaining 4:28 RBU 100.0% UBU  83.9%
 1642463232/3631452160 (45.2%) @8.1x, remaining 4:21 RBU 100.0% UBU  83.9%
 1679556608/3631452160 (46.3%) @8.0x, remaining 4:15 RBU 100.0% UBU  83.9%
 1716649984/3631452160 (47.3%) @8.0x, remaining 4:08 RBU 100.0% UBU  83.9%
 1753743360/3631452160 (48.3%) @8.0x, remaining 4:01 RBU 100.0% UBU  83.9%
 1790902272/3631452160 (49.3%) @8.0x, remaining 3:56 RBU 100.0% UBU  83.9%
 1828028416/3631452160 (50.3%) @8.0x, remaining 3:49 RBU 100.0% UBU  83.9%
 1865154560/3631452160 (51.4%) @8.0x, remaining 3:43 RBU 100.0% UBU  83.9%
 1902247936/3631452160 (52.4%) @8.0x, remaining 3:38 RBU 100.0% UBU  83.9%
 1939341312/3631452160 (53.4%) @8.0x, remaining 3:32 RBU 100.0% UBU  83.9%
 1976434688/3631452160 (54.4%) @8.0x, remaining 3:25 RBU 100.0% UBU  83.9%
 2013528064/3631452160 (55.4%) @8.0x, remaining 3:20 RBU 100.0% UBU  83.9%
 2050686976/3631452160 (56.5%) @8.0x, remaining 3:15 RBU 100.0% UBU  83.9%
 2087845888/3631452160 (57.5%) @8.0x, remaining 3:09 RBU 100.0% UBU  83.9%
 2124939264/3631452160 (58.5%) @8.0x, remaining 3:04 RBU 100.0% UBU  83.9%
 2162032640/3631452160 (59.5%) @8.0x, remaining 2:58 RBU 100.0% UBU  83.9%
 2199126016/3631452160 (60.6%) @8.0x, remaining 2:53 RBU 100.0% UBU  83.9%
 2236219392/3631452160 (61.6%) @8.0x, remaining 2:48 RBU 100.0% UBU  83.9%
 2273443840/3631452160 (62.6%) @8.0x, remaining 2:43 RBU 100.0% UBU  83.9%
 2304016384/3631452160 (63.4%) @6.6x, remaining 2:39 RBU 100.0% UBU  83.9%
 2341109760/3631452160 (64.5%) @8.0x, remaining 2:34 RBU 100.0% UBU  90.8%
 2378268672/3631452160 (65.5%) @8.0x, remaining 2:29 RBU 100.0% UBU  90.8%
 2415394816/3631452160 (66.5%) @8.0x, remaining 2:23 RBU 100.0% UBU  90.8%
 2452520960/3631452160 (67.5%) @8.0x, remaining 2:19 RBU 100.0% UBU  90.8%
 2489614336/3631452160 (68.6%) @8.0x, remaining 2:14 RBU 100.0% UBU  90.8%
 2526707712/3631452160 (69.6%) @8.0x, remaining 2:09 RBU 100.2% UBU  90.8%
 2563899392/3631452160 (70.6%) @8.1x, remaining 2:04 RBU 100.0% UBU  90.8%
 2601025536/3631452160 (71.6%) @8.0x, remaining 2:00 RBU 100.0% UBU  90.8%
 2638118912/3631452160 (72.6%) @8.0x, remaining 1:55 RBU 100.0% UBU  90.8%
 2675245056/3631452160 (73.7%) @8.0x, remaining 1:50 RBU  99.8% UBU  90.8%
 2712371200/3631452160 (74.7%) @8.0x, remaining 1:46 RBU 100.0% UBU  90.8%
 2749497344/3631452160 (75.7%) @8.0x, remaining 1:41 RBU 100.0% UBU  90.8%
 2786623488/3631452160 (76.7%) @8.0x, remaining 1:37 RBU 100.0% UBU  90.8%
 2823749632/3631452160 (77.8%) @8.0x, remaining 1:32 RBU 100.0% UBU  90.8%
 2854387712/3631452160 (78.6%) @6.6x, remaining 1:28 RBU 100.0% UBU  90.8%
 2891481088/3631452160 (79.6%) @8.0x, remaining 1:24 RBU 100.0% UBU  90.8%
 2928574464/3631452160 (80.6%) @8.0x, remaining 1:19 RBU 100.0% UBU  90.8%
 2965700608/3631452160 (81.7%) @8.0x, remaining 1:15 RBU 100.0% UBU  90.8%
 3002859520/3631452160 (82.7%) @8.0x, remaining 1:11 RBU  99.8% UBU  90.8%
 3039985664/3631452160 (83.7%) @8.0x, remaining 1:06 RBU 100.0% UBU  90.8%
 3077079040/3631452160 (84.7%) @8.0x, remaining 1:02 RBU 100.0% UBU  90.8%
 3114172416/3631452160 (85.8%) @8.0x, remaining 0:58 RBU 100.0% UBU  90.8%
 3151265792/3631452160 (86.8%) @8.0x, remaining 0:53 RBU 100.0% UBU  90.8%
 3188359168/3631452160 (87.8%) @8.0x, remaining 0:49 RBU 100.0% UBU  90.8%
 3225485312/3631452160 (88.8%) @8.0x, remaining 0:45 RBU 100.0% UBU  90.8%
 3262611456/3631452160 (89.8%) @8.0x, remaining 0:41 RBU 100.0% UBU  90.8%
 3299770368/3631452160 (90.9%) @8.0x, remaining 0:36 RBU 100.0% UBU  90.8%
 3336863744/3631452160 (91.9%) @8.0x, remaining 0:32 RBU 100.0% UBU  90.8%
 3373957120/3631452160 (92.9%) @8.0x, remaining 0:28 RBU 100.0% UBU  90.8%
 3411050496/3631452160 (93.9%) @8.0x, remaining 0:24 RBU 100.0% UBU  90.8%
 3448143872/3631452160 (95.0%) @8.0x, remaining 0:20 RBU 100.0% UBU  90.8%
 3478814720/3631452160 (95.8%) @6.6x, remaining 0:16 RBU 100.0% UBU  90.8%
 3515908096/3631452160 (96.8%) @8.0x, remaining 0:12 RBU 100.0% UBU  90.8%
 3553034240/3631452160 (97.8%) @8.0x, remaining 0:08 RBU 100.0% UBU  90.8%
 3583442944/3631452160 (98.7%) @6.6x, remaining 0:05 RBU 100.0% UBU  90.8%
:-[ WRITE@LBA=1ab2e0h failed with SK=3h/ASC=02h/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: updating RMA
/dev/scd0: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1773170 -use-the-force-luke=dummy -dvd-compat -speed=8 -overburn -use-the-force-luke=bufsize:32m

---

### Post by arvevans on 2007-12-04
I am another user with K3B Hang problems at end of a burn.  My CD burns but hangs instead of doing the VERIFY phase.  

Here is the Debug Info:

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
Optiarc DVD RW AD-7170A 1.02 (/dev/hda, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump]

K3bIsoImager
-----------------------
mkisofs print size result: 8364 (17129472 bytes)
Pipe throughput: 17129472 bytes read, 17129472 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/hda'
devname: '/dev/hda'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'Optiarc '
Identification : 'DVD RW AD-7170A '
Revision       : '1.02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) (current)
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 890880 = 870 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 8467 KB/s
Track 01: data    16 MB        
Total size:       18 MB (01:51.54) = 8366 sectors
Lout start:       19 MB (01:53/41) = 8366 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 351483
Starting to write CD/DVD at speed  48.0 in real TAO mode for multi session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of   16 MB written.
Track 01:    1 of   16 MB written (fifo 100%) [buf 100%]   3.0x.
Track 01:    2 of   16 MB written (fifo 100%) [buf 100%]   6.4x.
Track 01:    3 of   16 MB written (fifo 100%) [buf 100%]  22.4x.
Track 01:    4 of   16 MB written (fifo 100%) [buf 100%]  21.7x.
Track 01:    5 of   16 MB written (fifo 100%) [buf 100%]  22.5x.
Track 01:    6 of   16 MB written (fifo 100%) [buf 100%]  21.8x.
Track 01:    7 of   16 MB written (fifo 100%) [buf 100%]  22.6x.
Track 01:    8 of   16 MB written (fifo 100%) [buf 100%]  21.9x.
Track 01:    9 of   16 MB written (fifo 100%) [buf 100%]  22.7x.
Track 01:   10 of   16 MB written (fifo 100%) [buf 100%]  22.0x.
Track 01:   11 of   16 MB written (fifo 100%) [buf 100%]  22.8x.
Track 01:   12 of   16 MB written (fifo 100%) [buf 100%]  22.1x.
Track 01:   13 of   16 MB written (fifo 100%) [buf 100%]  22.9x.
Track 01:   14 of   16 MB written (fifo 100%) [buf 100%]  22.2x.
Track 01:   15 of   16 MB written (fifo 100%) [buf 100%]  22.9x.
Track 01:   16 of   16 MB written (fifo 100%) [buf 100%]  22.3x.
Track 01: Total bytes read/written: 17129472/17129472 (8364 sectors).
Writing  time:   25.127s
Average write speed  12.2x.
Min drive buffer fill was 100%
Fixating...
Fixating time:   24.801s
/usr/bin/wodim: fifo had 270 puts and 270 gets.
/usr/bin/wodim: fifo was 0 times empty and 61 times full, min fill was 93%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/hda speed=48 -tao driveropts=burnfree -eject -multi -xa -tsize=8364s - 

mkisofs
-----------------------
8364
I: -input-charset not specified, using utf-8 (detected in locale settings)
  6.11% done, estimate finish Tue Dec  4 13:20:15 2007
 12.04% done, estimate finish Tue Dec  4 13:20:15 2007
 17.97% done, estimate finish Tue Dec  4 13:20:15 2007
 24.09% done, estimate finish Tue Dec  4 13:20:15 2007
 30.02% done, estimate finish Tue Dec  4 13:20:15 2007
 35.95% done, estimate finish Tue Dec  4 13:20:15 2007
 41.88% done, estimate finish Tue Dec  4 13:20:15 2007
 48.00% done, estimate finish Tue Dec  4 13:20:15 2007
 53.93% done, estimate finish Tue Dec  4 13:20:15 2007
 59.86% done, estimate finish Tue Dec  4 13:20:15 2007
 65.79% done, estimate finish Tue Dec  4 13:20:15 2007
 71.92% done, estimate finish Tue Dec  4 13:20:15 2007
 77.85% done, estimate finish Tue Dec  4 13:20:40 2007
 83.78% done, estimate finish Tue Dec  4 13:20:40 2007
 89.77% done, estimate finish Tue Dec  4 13:20:39 2007
 95.70% done, estimate finish Tue Dec  4 13:20:37 2007
Total translation table size: 0
Total rockridge attributes bytes: 452
Total directory bytes: 696
Path table size(bytes): 10
Max brk space used 0
8364 extents written (16 MB)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid wg111v3_1_1_0_setup -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-arv/k3bS9Agua.tmp -rational-rock -hide-list /tmp/kde-arv/k3bJOVEKa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-arv/k3bfcdiwa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-arv/k3bjWaRYa.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid wg111v3_1_1_0_setup -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-arv/k3b6k9Eia.tmp -rational-rock -hide-list /tmp/kde-arv/k3bTLlUva.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-arv/k3b0NIE2a.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-arv/k3bDTg4zb.tmp

---

### Post by Johnny3 on 2007-12-16
Try tuning of do not eject medium after write process put and x by it.
settings/configure K3b/ advanced. I am new to Ubuntu. But it worker for me.
Johnny3 
Gainesville, Fl

---

### Post by Dr.Ninethousand on 2008-03-09
my k3b also crashes most of the time instead of verifying..  the discs are usually correct but I would like to fix this obviously..

anyone?

---

