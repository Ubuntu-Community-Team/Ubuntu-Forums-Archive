---
title: "Burning 64 bit kubuntu 16.04.4 LTS using kb3"
date: 2018-03-15
forum: General Help
---

### Post by anon_private on 2018-03-15
Hello,

I downloaded the iso file and the checksum was correct

I used kb3 to first simulate the burn. It was successful.

I then burned the file to the DVD -R. The writing was successful,  according to k3b, but the verification came back with an error (Elapsed  Time 3min 58s). When burning the 32 bit version I received no errors.

I give the ouput from the log below:

```
#Burned media
-----------------------
DVD-R Sequential

Devices
-----------------------
HL-DT-ST DVD+-RW GSA-H31N B109 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM,  DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential,  DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R  Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R,  RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

K3b::DataTrackReader
-----------------------
reading sectors 0 to 790743 with sector size 2048. Length: 790744 sectors, 1619443712 bytes.

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.13.3
QT Version:  4.8.6
Kernel:      4.4.0-116-generic

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: engaging DVD-R DAO upon user request...
/dev/sr0: reserving 790744 blocks
/dev/sr0: "Current Write Speed" is 16.4x1352KBps.
     0/1619443712 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
=== last message repeated 21 times. ===
10485760/1619443712 ( 0.6%) @2.3x, remaining 189:14 RBU 100.0% UBU   7.0%
41648128/1619443712 ( 2.6%) @6.7x, remaining 48:37 RBU 100.0% UBU  83.9%
73269248/1619443712 ( 4.5%) @6.8x, remaining 28:29 RBU 100.0% UBU  83.9%
105447424/1619443712 ( 6.5%) @7.0x, remaining 20:06 RBU 100.0% UBU  83.9%
138084352/1619443712 ( 8.5%) @7.1x, remaining 15:33 RBU 100.0% UBU  83.9%
171180032/1619443712 (10.6%) @7.2x, remaining 12:49 RBU 100.0% UBU  83.9%
204832768/1619443712 (12.6%) @7.3x, remaining 10:49 RBU 100.0% UBU  83.9%
238944256/1619443712 (14.8%) @7.4x, remaining 9:20 RBU 100.0% UBU  83.9%
273547264/1619443712 (16.9%) @7.5x, remaining 8:16 RBU 100.0% UBU  83.9%
308609024/1619443712 (19.1%) @7.6x, remaining 7:21 RBU 100.0% UBU  83.9%
344195072/1619443712 (21.3%) @7.7x, remaining 6:36 RBU 100.0% UBU  83.9%
380239872/1619443712 (23.5%) @7.8x, remaining 6:01 RBU 100.0% UBU  83.9%
416776192/1619443712 (25.7%) @7.9x, remaining 5:28 RBU 100.0% UBU  83.9%
453771264/1619443712 (28.0%) @8.0x, remaining 5:00 RBU 100.0% UBU  83.9%
491323392/1619443712 (30.3%) @8.1x, remaining 4:37 RBU 100.0% UBU  83.9%
522354688/1619443712 (32.3%) @6.7x, remaining 4:20 RBU 100.0% UBU  83.9%
560791552/1619443712 (34.6%) @8.3x, remaining 3:59 RBU 100.0% UBU  86.2%
599621632/1619443712 (37.0%) @8.4x, remaining 3:42 RBU 100.0% UBU  86.2%
639074304/1619443712 (39.5%) @8.5x, remaining 3:25 RBU 100.0% UBU  86.2%
678920192/1619443712 (41.9%) @8.6x, remaining 3:09 RBU 100.0% UBU  86.2%
719323136/1619443712 (44.4%) @8.7x, remaining 2:56 RBU  99.9% UBU  86.2%
760184832/1619443712 (46.9%) @8.9x, remaining 2:42 RBU 100.0% UBU  86.2%
801505280/1619443712 (49.5%) @8.9x, remaining 2:30 RBU 100.0% UBU  86.2%
843350016/1619443712 (52.1%) @9.1x, remaining 2:18 RBU 100.0% UBU  86.2%
885653504/1619443712 (54.7%) @9.2x, remaining 2:07 RBU 100.0% UBU  86.2%
928481280/1619443712 (57.3%) @9.3x, remaining 1:56 RBU 100.0% UBU  86.2%
971800576/1619443712 (60.0%) @9.4x, remaining 1:47 RBU 100.0% UBU  86.2%
1015611392/1619443712 (62.7%) @9.5x, remaining 1:37 RBU 100.0% UBU  86.2%
1059913728/1619443712 (65.4%) @9.6x, remaining 1:28 RBU 100.0% UBU  86.2%
1104642048/1619443712 (68.2%) @9.7x, remaining 1:19 RBU 100.0% UBU  86.2%
1149894656/1619443712 (71.0%) @9.8x, remaining 1:11 RBU 100.0% UBU  86.2%
1195671552/1619443712 (73.8%) @9.9x, remaining 1:02 RBU 100.0% UBU  86.2%
1241874432/1619443712 (76.7%) @10.0x, remaining 0:55 RBU 100.0% UBU  86.2%
1288568832/1619443712 (79.6%) @10.1x, remaining 0:47 RBU 100.0% UBU  86.2%
1335787520/1619443712 (82.5%) @10.2x, remaining 0:39 RBU 100.0% UBU  86.2%
1383464960/1619443712 (85.4%) @10.3x, remaining 0:32 RBU 100.0% UBU  86.2%
1431666688/1619443712 (88.4%) @10.4x, remaining 0:25 RBU 100.0% UBU  86.2%
1477902336/1619443712 (91.3%) @10.0x, remaining 0:18 RBU 100.0% UBU  86.2%
1522466816/1619443712 (94.0%) @9.6x, remaining 0:12 RBU 100.0% UBU  88.5%
1572012032/1619443712 (97.1%) @10.7x, remaining 0:06 RBU 100.0% UBU  88.5%
```

growisofs command:
-----------------------
```
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray  -use-the-force-luke=tty -use-the-force-luke=4gms  -use-the-force-luke=tracksize:790744 -use-the-force-luke=dao:790744  -dvd-compat -speed=16 -use-the-force-luke=bufsize:32m
```


I need advice regarding the next step.

Thanks

---

### Post by anon_private on 2018-03-15
UPDATE.

I put the DVD -R back in the drive and it said Blank Disk.

I attempted to burn again and, again, I received the Time Elapsed Error.

I attempted a re-burn, but this time I slowed the burning speed to 4x, again I received an error (Write Error and Time Elapsed - as I recall)

I don't know what's on the disk, but I may have made a coaster.

I am waiting for advice so that I don't waste another DVD -R.

I am wondering if the way forward is to burn using a new DVD -R at 4x?

Maybe my machine will not burn software rated at 64bit?

What do you think.

Regards

---

### Post by missmoondog on 2018-03-15
you should always burn iso's at a lower speed to help avoid errors. 

not sure about your drive, but most of my computers drive's don't like the dvd -r disc's. i can only use dvd +r's.

have never had an issue burning 32bit or 64bit disc's on any machine.

not much help, but just thought i'd throw that at you.

---

### Post by #&amp;thj^% on 2018-03-15
And one more thought here was finalize the dvd checked?
Some DVD/CD drives would not read if the session was not finalized.

---

### Post by anon_private on 2018-03-15
Thank you for the response.

I agree that the slower the burn rate the better.

How can I check if the DVD -R is finalised?

Regards.

PS. Nice dog

---

### Post by missmoondog on 2018-03-15
i believe k3b finalizes the burn automatically, when burning an iso, doesn't it? but there should be an option in the settings some where to make sure.

are you clicking the blue bar that says more options and clicking burn image? never mind that part. i see there's the option to burn iso under tools also, in case you do it that way.

edit:
i lied up above! the dvd's i have ARE dvd -r's. sorry about that. it's the dvd-r+ that i can't use. haven't burned a dvd in a while. forgot what i had. :(

edit 2:
i don't see any place for option to close disc when trying to burn an iso. next to positive it does that automatically though. if the 32bit version burned correctly, it closed the disc it if try's to run when you use it. just curious. have you tried burning with xfburn? that was the default burner in my lubuntu anyway. it works pretty good.

---

### Post by #&amp;thj^% on 2018-03-15
> **anon_private said:**
> 
Nice Dog

Thanks He is my Bud, and a keeper for sure! :)
> **anon_private said:**
> Thank you for the response.

How can I check if the DVD -R is finalised?

Regards.



You know I just may be speaking out my back-side here.
It has been many years since I last used K3b, with the progressing times I have not found the need to use such a heavy application like K3b.
Most all i do now is through USB writers and rare occasions that I need  to write a CD/DVD disk I just use Xfburn, but I just installed K3b to check and errors out the ying yang!
```
Devices
-----------------------
hp PLDS DVDRW  DU8AESH 6HS3 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::DataTrackReader
-----------------------
reading sectors 0 to 112882 with sector size 2048. Length: 112883 sectors, 231184384 bytes.
using buffer size of 64 blocks.
Problem while reading. Retrying from sector 63872.
Problem while reading. Retrying from sector 64256.
Problem while reading. Retrying from sector 64768.
Read error in sector 64792.
Read a total of 64768 sectors (132644864 bytes)

System
-----------------------
K3b Version: 17.12.3
KDE Version: 5.43.0
Qt Version:  5.10.1
Kernel:      4.15.9-1-ARCH

Used versions
-----------------------
cdrecord: 3.2a09

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
cdrecord: Warning: Cannot read drive buffer.
cdrecord: Warning: The DMA speed test has been skipped.
Cdrecord-ProDVD-ProBD-Clone 3.02a09 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2016 Joerg Schilling
TOC Type: 1 = CD-ROM
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'hp PLDS '
Identifikation : 'DVDRW  DU8AESH  '
Revision       : '6HS3'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: CD-RW
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-R/DL sequential recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-RAM 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW (current)
Profile: CD-R 
Profile: CD-ROM 
Profile: Removable Disk 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 335104 = 327 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   220 MB        
Total size:      253 MB (25:05.10) = 112883 sectors
Lout start:      253 MB (25:07/08) = 112883 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Reference speed: 2
Disk Is not unrestricted
Disk Is erasable
  ATIP start of lead in:  -11745 (97:25/30)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 4 6
  recommended erase/write power: 3
  A1 values: 02 4C B0
  A2 values: 5C D8 36
Disk type:    Phase change
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
    Capacity  Blklen/Sparesz.  Format-type  Type
      359849             2048         0x00  Unformated or Blank Media
      295264               32         0x10  Reserved (0)
           0               32         0x11  Reserved (0)
           0               32         0x12  Reserved (0)
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 246966
Forcespeed is OFF.
Starting to write CD/DVD/BD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
cdrecord: WARNING: Drive returns wrong startsec (0) using -150
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  220 MB written.
Track 01:    1 of  220 MB written (fifo 100%) [buf  81%]   3.9x.
Track 01:    2 of  220 MB written (fifo 100%) [buf  84%]   4.2x.
Track 01:    3 of  220 MB written (fifo 100%) [buf  83%]   4.2x.
Track 01:    4 of  220 MB written (fifo 100%) [buf 100%]   4.3x.
Track 01:    5 of  220 MB written (fifo 100%) [buf  92%]   4.2x.
Track 01:    6 of  220 MB written (fifo 100%) [buf  88%]   4.1x.
Track 01:    7 of  220 MB written (fifo 100%) [buf  85%]   4.2x.
Track 01:    8 of  220 MB written (fifo 100%) [buf 100%]   4.3x.
Track 01:    9 of  220 MB written (fifo 100%) [buf  93%]   4.2x.
Track 01:   10 of  220 MB written (fifo 100%) [buf  88%]   4.0x.
Track 01:   11 of  220 MB written (fifo 100%) [buf  89%]   4.2x.
Track 01:   12 of  220 MB written (fifo 100%) [buf  88%]   4.1x.
Track 01:   13 of  220 MB written (fifo 100%) [buf  83%]   4.2x.
Track 01:   14 of  220 MB written (fifo 100%) [buf 100%]   4.3x.
Track 01:   15 of  220 MB written (fifo 100%) [buf 100%]   4.2x.
Track 01:   16 of  220 MB written (fifo 100%) [buf  97%]   4.0x.
Track 01:   17 of  220 MB written (fifo 100%) [buf  97%]   4.2x.
Track 01:   18 of  220 MB written (fifo 100%) [buf  82%]   3.9x.
Track 01:   19 of  220 MB written (fifo 100%) [buf  82%]   4.2x.
Track 01:   20 of  220 MB written (fifo 100%) [buf  83%]   4.1x.
Track 01:   21 of  220 MB written (fifo 100%) [buf  83%]   4.2x.
Track 01:   22 of  220 MB written (fifo 100%) [buf  82%]   4.0x.
Track 01:   23 of  220 MB written (fifo 100%) [buf  80%]   4.2x.
Track 01:   24 of  220 MB written (fifo 100%) [buf  85%]   4.1x.
Track 01:   25 of  220 MB written (fifo 100%) [buf  84%]   4.2x.
Track 01:   26 of  220 MB written (fifo 100%) [buf 100%]   4.2x.
Track 01:   27 of  220 MB written (fifo 100%) [buf  95%]   4.1x.
Track 01:   28 of  220 MB written (fifo 100%) [buf  91%]   4.0x.
Track 01:   29 of  220 MB written (fifo 100%) [buf  94%]   4.2x.
Track 01:   30 of  220 MB written (fifo 100%) [buf  93%]   4.0x.
Track 01:   31 of  220 MB written (fifo 100%) [buf  94%]   4.1x.
Track 01:   32 of  220 MB written (fifo 100%) [buf  89%]   4.0x.
Track 01:   33 of  220 MB written (fifo 100%) [buf  86%]   4.1x.
Track 01:   34 of  220 MB written (fifo 100%) [buf  96%]   4.4x.
Track 01:   35 of  220 MB written (fifo 100%) [buf  89%]   4.0x.
Track 01:   36 of  220 MB written (fifo 100%) [buf  90%]   4.3x.
Track 01:   37 of  220 MB written (fifo 100%) [buf  89%]   4.1x.
Track 01:   38 of  220 MB written (fifo 100%) [buf  84%]   4.2x.
Track 01:   39 of  220 MB written (fifo 100%) [buf  84%]   4.1x.
Track 01:   40 of  220 MB written (fifo 100%) [buf  85%]   4.2x.
Track 01:   41 of  220 MB written (fifo 100%) [buf  90%]   4.1x.
Track 01:   42 of  220 MB written (fifo 100%) [buf  96%]   4.3x.
Track 01:   43 of  220 MB written (fifo 100%) [buf  97%]   4.1x.
Track 01:   44 of  220 MB written (fifo 100%) [buf  98%]   4.2x.
Track 01:   45 of  220 MB written (fifo 100%) [buf  98%]   4.1x.
Track 01:   46 of  220 MB written (fifo 100%) [buf  83%]   4.0x.
Track 01:   47 of  220 MB written (fifo 100%) [buf  97%]   4.2x.
Track 01:   48 of  220 MB written (fifo 100%) [buf  96%]   4.2x.
Track 01:   49 of  220 MB written (fifo 100%) [buf  91%]   4.0x.
Track 01:   50 of  220 MB written (fifo 100%) [buf  94%]   4.2x.
Track 01:   51 of  220 MB written (fifo 100%) [buf  91%]   4.0x.
Track 01:   52 of  220 MB written (fifo 100%) [buf  88%]   4.1x.
Track 01:   53 of  220 MB written (fifo 100%) [buf  83%]   4.0x.
Track 01:   54 of  220 MB written (fifo 100%) [buf 100%]   4.4x.
Track 01:   55 of  220 MB written (fifo 100%) [buf 100%]   4.0x.
Track 01:   56 of  220 MB written (fifo 100%) [buf  95%]   4.1x.
Track 01:   57 of  220 MB written (fifo 100%) [buf  94%]   4.0x.
Track 01:   58 of  220 MB written (fifo 100%) [buf  93%]   4.1x.
Track 01:   59 of  220 MB written (fifo 100%) [buf  87%]   4.0x.
Track 01:   60 of  220 MB written (fifo 100%) [buf  86%]   4.1x.
Track 01:   61 of  220 MB written (fifo 100%) [buf  98%]   4.1x.
Track 01:   62 of  220 MB written (fifo 100%) [buf  86%]   4.0x.
Track 01:   63 of  220 MB written (fifo 100%) [buf 100%]   4.2x.
Track 01:   64 of  220 MB written (fifo 100%) [buf  95%]   4.1x.
Track 01:   65 of  220 MB written (fifo 100%) [buf  87%]   4.2x.
Track 01:   66 of  220 MB written (fifo 100%) [buf  85%]   4.1x.
Track 01:   67 of  220 MB written (fifo 100%) [buf  82%]   4.2x.
Track 01:   68 of  220 MB written (fifo 100%) [buf  96%]   4.3x.
Track 01:   69 of  220 MB written (fifo 100%) [buf  90%]   4.2x.
Track 01:   70 of  220 MB written (fifo 100%) [buf  86%]   4.1x.
Track 01:   71 of  220 MB written (fifo 100%) [buf  83%]   4.2x.
Track 01:   72 of  220 MB written (fifo 100%) [buf  98%]   4.3x.
Track 01:   73 of  220 MB written (fifo 100%) [buf  87%]   4.1x.
Track 01:   74 of  220 MB written (fifo 100%) [buf  85%]   4.1x.
Track 01:   75 of  220 MB written (fifo 100%) [buf 100%]   4.4x.
Track 01:   76 of  220 MB written (fifo 100%) [buf  91%]   4.0x.
Track 01:   77 of  220 MB written (fifo 100%) [buf  91%]   4.2x.
Track 01:   78 of  220 MB written (fifo 100%) [buf  82%]   4.0x.
Track 01:   79 of  220 MB written (fifo 100%) [buf  84%]   4.2x.
Track 01:   80 of  220 MB written (fifo 100%) [buf  96%]   4.2x.
Track 01:   81 of  220 MB written (fifo 100%) [buf  94%]   4.2x.
Track 01:   82 of  220 MB written (fifo 100%) [buf  89%]   4.0x.
Track 01:   83 of  220 MB written (fifo 100%) [buf  91%]   4.2x.
Track 01:   84 of  220 MB written (fifo 100%) [buf  88%]   4.0x.
Track 01:   85 of  220 MB written (fifo 100%) [buf  88%]   4.2x.
Track 01:   86 of  220 MB written (fifo 100%) [buf  86%]   4.0x.
Track 01:   87 of  220 MB written (fifo 100%) [buf 100%]   4.3x.
Track 01:   88 of  220 MB written (fifo 100%) [buf  93%]   4.0x.
Track 01:   89 of  220 MB written (fifo 100%) [buf  91%]   4.1x.
Track 01:   90 of  220 MB written (fifo 100%) [buf  81%]   3.9x.
Track 01:   91 of  220 MB written (fifo 100%) [buf 100%]   4.4x.
Track 01:   92 of  220 MB written (fifo 100%) [buf  98%]   4.0x.
Track 01:   93 of  220 MB written (fifo 100%) [buf  90%]   4.0x.
Track 01:   94 of  220 MB written (fifo 100%) [buf  86%]   4.0x.
Track 01:   95 of  220 MB written (fifo 100%) [buf  82%]   4.1x.
Track 01:   96 of  220 MB written (fifo  98%) [buf 100%]   4.5x.
Track 01:   97 of  220 MB written (fifo 100%) [buf  93%]   4.0x.
Track 01:   98 of  220 MB written (fifo 100%) [buf  94%]   4.3x.
Track 01:   99 of  220 MB written (fifo 100%) [buf  85%]   4.0x.
Track 01:  100 of  220 MB written (fifo 100%) [buf  82%]   4.2x.
Track 01:  101 of  220 MB written (fifo 100%) [buf  97%]   4.3x.
Track 01:  102 of  220 MB written (fifo 100%) [buf  91%]   4.2x.
Track 01:  103 of  220 MB written (fifo 100%) [buf  91%]   4.1x.
Track 01:  104 of  220 MB written (fifo 100%) [buf  89%]   4.2x.
Track 01:  105 of  220 MB written (fifo 100%) [buf  88%]   4.1x.
Track 01:  106 of  220 MB written (fifo 100%) [buf  87%]   4.2x.
Track 01:  107 of  220 MB written (fifo 100%) [buf  85%]   4.1x.
Track 01:  108 of  220 MB written (fifo 100%) [buf  88%]   4.2x.
Track 01:  109 of  220 MB written (fifo 100%) [buf  83%]   4.0x.
Track 01:  110 of  220 MB written (fifo 100%) [buf  81%]   4.2x.
Track 01:  111 of  220 MB written (fifo 100%) [buf  97%]   4.2x.
Track 01:  112 of  220 MB written (fifo 100%) [buf 100%]   4.2x.
Track 01:  113 of  220 MB written (fifo 100%) [buf  96%]   4.0x.
Track 01:  114 of  220 MB written (fifo 100%) [buf  95%]   4.2x.
Track 01:  115 of  220 MB written (fifo 100%) [buf  94%]   4.0x.
Track 01:  116 of  220 MB written (fifo 100%) [buf  96%]   4.2x.
Track 01:  117 of  220 MB written (fifo 100%) [buf  94%]   4.0x.
Track 01:  118 of  220 MB written (fifo 100%) [buf  93%]   4.2x.
Track 01:  119 of  220 MB written (fifo 100%) [buf  85%]   4.0x.
Track 01:  120 of  220 MB written (fifo 100%) [buf  97%]   4.3x.
Track 01:  121 of  220 MB written (fifo 100%) [buf 100%]   4.0x.
Track 01:  122 of  220 MB written (fifo 100%) [buf  97%]   4.1x.
Track 01:  123 of  220 MB written (fifo 100%) [buf  96%]   4.0x.
Track 01:  124 of  220 MB written (fifo 100%) [buf  88%]   4.0x.
Track 01:  125 of  220 MB written (fifo 100%) [buf  83%]   4.0x.
Track 01:  126 of  220 MB written (fifo 100%) [buf  96%]   4.3x.
Track 01:  127 of  220 MB written (fifo 100%) [buf  91%]   4.2x.
Track 01:  128 of  220 MB written (fifo 100%) [buf  87%]   4.1x.
Track 01:  129 of  220 MB written (fifo 100%) [buf  80%]   4.2x.
Track 01:  130 of  220 MB written (fifo 100%) [buf  99%]   4.3x.
Track 01:  131 of  220 MB written (fifo 100%) [buf  83%]   4.1x.
Track 01:  132 of  220 MB written (fifo 100%) [buf  82%]   4.1x.
Track 01:  133 of  220 MB written (fifo 100%) [buf  99%]   4.4x.
Track 01:  134 of  220 MB written (fifo 100%) [buf  96%]   4.1x.
Track 01:  135 of  220 MB written (fifo 100%) [buf  91%]   4.2x.
Track 01:  136 of  220 MB written (fifo 100%) [buf  81%]   4.0x.
Track 01:  137 of  220 MB written (fifo 100%) [buf  79%]   4.2x.
Track 01:  138 of  220 MB written (fifo 100%) [buf  96%]   4.3x.
Track 01:  139 of  220 MB written (fifo 100%) [buf  91%]   4.2x.
Track 01:  140 of  220 MB written (fifo 100%) [buf  87%]   4.0x.
Track 01:  141 of  220 MB written (fifo 100%) [buf  83%]   4.1x.
Track 01:  142 of  220 MB written (fifo 100%) [buf 100%]   4.2x.
Track 01:  143 of  220 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:  144 of  220 MB written (fifo 100%) [buf  93%]   4.0x.
Track 01:  145 of  220 MB written (fifo 100%) [buf  91%]   4.2x.
Track 01:  146 of  220 MB written (fifo 100%) [buf  81%]   3.9x.
Track 01:  147 of  220 MB written (fifo 100%) [buf  99%]   4.4x.
Track 01:  148 of  220 MB written (fifo 100%) [buf  96%]   4.0x.
Track 01:  149 of  220 MB written (fifo 100%) [buf  96%]   4.2x.
Track 01:  150 of  220 MB written (fifo 100%) [buf  92%]   4.0x.
Track 01:  151 of  220 MB written (fifo 100%) [buf  91%]   4.1x.
Track 01:  152 of  220 MB written (fifo 100%) [buf  83%]   3.9x.
Track 01:  153 of  220 MB written (fifo 100%) [buf  98%]   4.3x.
Track 01:  154 of  220 MB written (fifo 100%) [buf  93%]   4.0x.
Track 01:  155 of  220 MB written (fifo 100%) [buf  87%]   4.1x.
Track 01:  156 of  220 MB written (fifo 100%) [buf  79%]   3.9x.
Track 01:  157 of  220 MB written (fifo 100%) [buf  99%]   4.3x.
Track 01:  158 of  220 MB written (fifo 100%) [buf  80%]   4.0x.
Track 01:  159 of  220 MB written (fifo 100%) [buf  85%]   4.2x.
Track 01:  160 of  220 MB written (fifo 100%) [buf  99%]   4.4x.
Track 01:  161 of  220 MB written (fifo 100%) [buf  90%]   4.0x.
Track 01:  162 of  220 MB written (fifo 100%) [buf  89%]   4.2x.
Track 01:  163 of  220 MB written (fifo 100%) [buf  92%]   4.1x.
Track 01:  164 of  220 MB written (fifo 100%) [buf  85%]   4.1x.
Track 01:  165 of  220 MB written (fifo 100%) [buf  80%]   4.0x.
Track 01:  166 of  220 MB written (fifo 100%) [buf  80%]   4.2x.
Track 01:  167 of  220 MB written (fifo 100%) [buf  94%]   4.2x.
Track 01:  168 of  220 MB written (fifo 100%) [buf  93%]   4.2x.
Track 01:  169 of  220 MB written (fifo 100%) [buf  88%]   4.0x.
Track 01:  170 of  220 MB written (fifo 100%) [buf  81%]   4.1x.
Track 01:  171 of  220 MB written (fifo 100%) [buf  99%]   4.3x.
Track 01:  172 of  220 MB written (fifo 100%) [buf  85%]   4.0x.
Track 01:  173 of  220 MB written (fifo 100%) [buf  88%]   4.1x.
Track 01:  174 of  220 MB written (fifo 100%) [buf  88%]   4.2x.
Track 01:  175 of  220 MB written (fifo 100%) [buf  82%]   4.0x.
Track 01:  176 of  220 MB written (fifo 100%) [buf  81%]   4.2x.
Track 01:  177 of  220 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:  178 of  220 MB written (fifo 100%) [buf  95%]   4.1x.
Track 01:  179 of  220 MB written (fifo 100%) [buf  85%]   3.9x.
Track 01:  180 of  220 MB written (fifo 100%) [buf  99%]   4.3x.
Track 01:  181 of  220 MB written (fifo 100%) [buf  92%]   4.0x.
Track 01:  182 of  220 MB written (fifo 100%) [buf  94%]   4.2x.
Track 01:  183 of  220 MB written (fifo 100%) [buf  93%]   4.0x.
Track 01:  184 of  220 MB written (fifo 100%) [buf  94%]   4.2x.
Track 01:  185 of  220 MB written (fifo 100%) [buf  89%]   4.0x.
Track 01:  186 of  220 MB written (fifo 100%) [buf  88%]   4.1x.
Track 01:  187 of  220 MB written (fifo 100%) [buf  85%]   4.0x.
Track 01:  188 of  220 MB written (fifo 100%) [buf  83%]   4.1x.
Track 01:  189 of  220 MB written (fifo 100%) [buf  80%]   4.2x.
Track 01:  190 of  220 MB written (fifo 100%) [buf  94%]   4.3x.
Track 01:  191 of  220 MB written (fifo 100%) [buf  92%]   4.2x.
Track 01:  192 of  220 MB written (fifo 100%) [buf  88%]   4.1x.
Track 01:  193 of  220 MB written (fifo 100%) [buf  88%]   4.2x.
Track 01:  194 of  220 MB written (fifo 100%) [buf  87%]   4.1x.
Track 01:  195 of  220 MB written (fifo 100%) [buf  89%]   4.3x.
Track 01:  196 of  220 MB written (fifo 100%) [buf  86%]   4.1x.
Track 01:  197 of  220 MB written (fifo 100%) [buf  88%]   4.2x.
Track 01:  198 of  220 MB written (fifo 100%) [buf  83%]   4.0x.
Track 01:  199 of  220 MB written (fifo 100%) [buf  99%]   4.4x.
Track 01:  200 of  220 MB written (fifo 100%) [buf  94%]   4.0x.
Track 01:  201 of  220 MB written (fifo 100%) [buf  86%]   4.1x.
Track 01:  202 of  220 MB written (fifo 100%) [buf  83%]   4.0x.
Track 01:  203 of  220 MB written (fifo 100%) [buf  83%]   4.2x.
Track 01:  204 of  220 MB written (fifo 100%) [buf  83%]   4.1x.
Track 01:  205 of  220 MB written (fifo 100%) [buf  99%]   4.4x.
Track 01:  206 of  220 MB written (fifo 100%) [buf  91%]   4.0x.
Track 01:  207 of  220 MB written (fifo 100%) [buf  91%]   4.2x.
Track 01:  208 of  220 MB written (fifo 100%) [buf  85%]   4.0x.
Track 01:  209 of  220 MB written (fifo 100%) [buf  81%]   4.1x.
Track 01:  210 of  220 MB written (fifo 100%) [buf  97%]   4.2x.
Track 01:  211 of  220 MB written (fifo 100%) [buf  94%]   4.1x.
Track 01:  212 of  220 MB written (fifo 100%) [buf  93%]   4.0x.
Track 01:  213 of  220 MB written (fifo 100%) [buf  94%]   4.2x.
Track 01:  214 of  220 MB written (fifo 100%) [buf  88%]   4.0x.
Track 01:  215 of  220 MB written (fifo 100%) [buf  89%]   4.2x.
Track 01:  216 of  220 MB written (fifo 100%) [buf  86%]   4.0x.
Track 01:  217 of  220 MB written (fifo 100%) [buf  88%]   4.2x.
Track 01:  218 of  220 MB written (fifo 100%) [buf  83%]   4.0x.
Track 01:  219 of  220 MB written (fifo 100%) [buf  77%]   4.1x.
Track 01:  220 of  220 MB written (fifo 100%) [buf  80%]   4.3x.
Track 01: Total bytes read/written: 231184384/231184384 (112883 sectors).
Writing  time:  416.481s (00:06:56.481)
Average write speed   3.6x.
Min drive buffer fill was 77%
Fixating...
Fixating time:   37.847s (00:00:37.847)
cdrecord: fifo had 3642 puts and 3642 gets.
cdrecord: fifo was 0 times empty and 3559 times full, min fill was 95%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/sbin/cdrecord -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -data -tsize=112883s -

```
So I Apologize here for misleading you. :(
But have you tried with Xfburn yet? Very light weight to the system.

---

### Post by scdbackup on 2018-03-16
Hi,

yeah, try Xfburn, so that my backend libburn gets a chance too.
This thread shows runs of growisofs and crecord as backend.

The growisofs run of the original post did not strive for keeping
the medium appendable. Option -dvd-compat told growisofs to close
the medium, option -use-the-force-luke=dao told it to use write
type Disk-At-Once (DAO).

There is a known and yet unfixed growisofs bug about DVD-R DAO
  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=794868](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=794868)
but that one is supposed to issue an error message rather than silently
ending at 97.1 percent of the burn job.
The image size of 790744 = 49421.5 DVD chunks would be able to trigger
the bug.


anon_private wrote:
> I put the DVD -R back in the drive and it said Blank Disk.

If K3B says blank disc, then the drive said blank disc.
This means that the table-of-content of the medium does not look
like it was written. But it does not necessarily mean that it is
possible to write to it again.

> Maybe my machine will not burn software rated at 64bit?

The content byte values of the burned image cannot cause a burn run to fail.
Its size can (by growisofs DAO bug or by simple overflow of medium).


missmoondog wrote:
> you should always burn iso's at a lower speed to help avoid errors. 

One can read this often. But to my experience as developer and owner
of seven drives, speed is not really decisive for success. (Unless the
drive lets the medium derail which makes a terrible noise.)

It's the general relation of drive and medium which causes most failure.
But in this case here, the early end of the growisofs log leaves room
for blaming to problem on the burn backend.


anon_private wrote:
> How can I check if the DVD -R is finalised?

```

dvd+rw-mediainfo /dev/sr0

```
should say among many other lines
```

READ DISC INFORMATION:
 Disc status:           complete

```


missmoondog wrote:
> i believe k3b finalizes the burn automatically, when burning an iso,
> doesn't it?

All burn backends i know of do finalize the session. The medium may be
kept appendable (unfinalized) in order to keep it ready for more
burn sessions on the yet unused medium area.

> i don't see any place for option to close disc when trying to burn an iso

There should rather be an option to keep it appendable. anon_private's
run ordered growisofs to use DAO. This implies that the medium shall get
closed and not stay appendable.


Proposals:

- Try Xfburn indeed, or look whether K3B accepts cdrskin as burn backend
  for DVD. (Newest versions should do.)
  Those runs would employ libburn as burning software.

- Switch your K3B to using crecord, as 1fallen did. cdrecord is not
  necessarily the best backend for DVD, but still better than a failing
  DVD-R DAO run with growisofs.

- Use DVD+R media instead of DVD-R. The growisofs bug (if it is the culprit)
  does only apply to DVD-r and unformatted DVD-RW.

Have a nice day :)

Thomas

---

### Post by anon_private on 2018-03-16
> **scdbackup said:**
> Hi,

yeah, try Xfburn, so that my backend libburn gets a chance too.
This thread shows runs of growisofs and crecord as backend.

The growisofs run of the original post did not strive for keeping
the medium appendable. Option -dvd-compat told growisofs to close
the medium, option -use-the-force-luke=dao told it to use write
type Disk-At-Once (DAO).

There is a known and yet unfixed growisofs bug about DVD-R DAO
  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=794868](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=794868)
but that one is supposed to issue an error message rather than silently
ending at 97.1 percent of the burn job.
The image size of 790744 = 49421.5 DVD chunks would be able to trigger
the bug.


anon_private wrote:
> I put the DVD -R back in the drive and it said Blank Disk.

If K3B says blank disc, then the drive said blank disc.
This means that the table-of-content of the medium does not look
like it was written. But it does not necessarily mean that it is
possible to write to it again.

> Maybe my machine will not burn software rated at 64bit?

The content byte values of the burned image cannot cause a burn run to fail.
Its size can (by growisofs DAO bug or by simple overflow of medium).


missmoondog wrote:
> you should always burn iso's at a lower speed to help avoid errors. 

One can read this often. But to my experience as developer and owner
of seven drives, speed is not really decisive for success. (Unless the
drive lets the medium derail which makes a terrible noise.)

It's the general relation of drive and medium which causes most failure.
But in this case here, the early end of the growisofs log leaves room
for blaming to problem on the burn backend.


anon_private wrote:
> How can I check if the DVD -R is finalised?

```

dvd+rw-mediainfo /dev/sr0

```
should say among many other lines
```

READ DISC INFORMATION:
 Disc status:           complete

```


missmoondog wrote:
> i believe k3b finalizes the burn automatically, when burning an iso,
> doesn't it?

All burn backends i know of do finalize the session. The medium may be
kept appendable (unfinalized) in order to keep it ready for more
burn sessions on the yet unused medium area.

> i don't see any place for option to close disc when trying to burn an iso

There should rather be an option to keep it appendable. anon_private's
run ordered growisofs to use DAO. This implies that the medium shall get
closed and not stay appendable.


Proposals:

- Try Xfburn indeed, or look whether K3B accepts cdrskin as burn backend
  for DVD. (Newest versions should do.)
  Those runs would employ libburn as burning software.

-ofs. Switch your K3B to using crecord, as 1fallen did. cdrecord is not
  necessarily the best backend for DVD, but still better than a failing
  DVD-R DAO run with growis

- Use DVD+R media instead of DVD-R. The growisofs bug (if it is the culprit)
  does only apply to DVD-r and unformatted DVD-RW.

Have a nice day :)

Thomas

 'Switch your K3B to using crecord, as 1fallen did. cdrecord is not
  necessarily the best backend for DVD, but still better than a failing
  DVD-R DAO run with growis'

I can't see how to switch to crecord

---

### Post by scdbackup on 2018-03-16
Hi,

> I can't see how to switch to crecord

With my olde K3B 2.0.2 there is: Settings -> Configure K3b... -> Programs
But i fail to do anything to the items underneath "cdrecord" and "growisofs".
Maybe 1fallen can tell how to switch from growisofs to cdrecord.

If not: try Xfburn.

Or in the shell one of these:
```

cdrskin -v dev=/dev/sr0 -eject /path/to/your/image.iso

xorriso -as cdrecord -v dev=/dev/sr0 -eject /path/to/your/image.iso

cdrecord -v dev=/dev/sr0 -eject /path/to/your/image.iso

```
Where you have to replace "/path/to/your/image.iso" by a file path
which leads to the ISO image you want to burn onto your DVD-R.
(I put cdrskin and xorriso first, because i can give support for them.)

Have a nice day :)

Thomas

---

### Post by #&amp;thj^% on 2018-03-16
> **anon_private said:**
> 'Switch your K3B to using crecord, as 1fallen did. cdrecord is not
  necessarily the best backend for DVD, but still better than a failing
  DVD-R DAO run with growis'

I can't see how to switch to crecord

you will need "dvd+rw-tools" and "cdrdao" installed and I beleive "K3b codecs".
But **"Please"** just try with Xfburn, so much simpler to work with. ;)

---

### Post by anon_private on 2018-03-16
> **scdbackup said:**
> Hi,

> I can't see how to switch to crecord

With my olde K3B 2.0.2 there is: Settings -> Configure K3b... -> Programs
But i fail to do anything to the items underneath "cdrecord" and "growisofs".
Maybe 1fallen can tell how to switch from growisofs to cdrecord.

If not: try Xfburn.

Or in the shell one of these:
```

cdrskin -v dev=/dev/sr0 -eject /path/to/your/image.iso

xorriso -as cdrecord -v dev=/dev/sr0 -eject /path/to/your/image.iso

cdrecord -v dev=/dev/sr0 -eject /path/to/your/image.iso

```
Where you have to replace "/path/to/your/image.iso" by a file path
which leads to the ISO image you want to burn onto your DVD-R.
(I put cdrskin and xorriso first, because i can give support for them.)

Have a nice day :)

Thomas

It does seem complicated.

I would prefer not to install any more software.

I have Brasero installed.

I may try to burn again using k3b, but this time slow the burn to 4x.

Evidently, k3b and Brasero are the preferred burning packages.

Interestingly, I had no trouble burning the previous iso file with k3b, and at 16x.

If I can pre-empt your next question, yes, I did verify the hashes prior to burning.

Best wishes

---

### Post by scdbackup on 2018-03-17
Hi,

it comes to me that if you tell K3b to keep the medium appendable then
it cannot employ growisofs with write type DAO and thus cannot trigger
the known growisofs DAO bug.


> I would prefer not to install any more software.

If the problem is with growisofs then you need at least another backend
software in order to burn DVD-R with write type DAO.

> Evidently, k3b and Brasero are the preferred burning packages.

They are frontends which do not burn optical media by themselves
but employ one of the backends.
Frontends provide a graphical user interface and often also conversion of
multi-media file formats.
But with burning an ISO image there is few benefit beyond the nice colorful
menus and buttons.

Installing a backend is much less effort than installing a GUI frontend
with its many supporting libraries. Try
```

apt-get install xorriso

```
On Debian 8 xorriso needs 45 libraries (mostly fundamental and already
installed), Xfburn needs 70, Brasero 118, and K3b needs 132 libraries.
As far as ISO 9660 is concerned, xorriso can outperform all three frontends,
especially when it comes to making backups of the hard disk.

> Interestingly, I had no trouble burning the previous iso file with k3b, and at 16x.

The growisofs DAO bug happens only if the number of blocks of the ISO
is not divisible by 16 and if the Linux kernel is young enough to take
offense from the last WRITE10 command if its sg_io_hdr.dxfer_len is 16
but the WRITE10 Transfer Length is less than 16.


> If I can pre-empt your next question, yes, I did verify the hashes prior to burning.

As said, the byte content does not influence the burn success, if only
the number of bytes fits onto the medium.
Bad downloads can spoil boot success but hardly burn success.

Have a nice day :)

Thomas

---

### Post by SeijiSensei on 2018-03-17
Might I suggest you use a USB drive instead of burning a DVD. It's a much easier way to build a boot disk. Either use the [native tool that comes with Ubuntu](https://help.ubuntu.com/community/Installation/FromUSBStick), or use [Rufus]("https://rufus.akeo.ie") on Windows.

---

### Post by anon_private on 2018-03-17
> **SeijiSensei said:**
> Might I suggest you use a USB drive instead of burning a DVD. It's a much easier way to build a boot disk. Either use the [native tool that comes with Ubuntu]("https://help.ubuntu.com/community/Installation/FromUSBStick"), or use [Rufus]("https://rufus.akeo.ie") on Windows.

I have now burned to a DVD -R using Brasero

'it comes to me that if you tell K3b to keep the medium appendable then
it cannot employ growisofs with write type DAO and thus cannot trigger
the known growisofs DAO bug.'

How would I do this?

Regards

---

### Post by scdbackup on 2018-03-17
Hi,

(I should not talk so much about K3b, as i hardly ever start any of the GUI
 frontends ...)

> > tell K3b to keep the medium appendable

> How would I do this?

After chosing "Burn Image" from the "More Actions" menu, i see option tabs 
"Settings" and "Advanced". In "Advanced" i see option "Start multisession CD". 
If we are lucky and it is valid for multi-session DVD too, then it should 
avoid write type DAO and rather cause DVD-R write type Incremental.


> I have now burned to a DVD -R using Brasero

Does the log talk of "BraseroLibburn" ?
The use of growisofs as backend would be indicated by "BraseroGrowisofs".
If it was growisofs then it would be interesting to see the log with the
growisofs arguments used. (Several "-use-the-force-luke=" should be to see.)

Have a nice day :)

Thomas

---

