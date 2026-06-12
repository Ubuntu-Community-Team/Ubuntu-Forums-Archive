---
title: "CD/DVD Burning Problems"
date: 2007-05-19
forum: General Help
---

### Post by IgnacioMiller on 2007-05-19
Hi all,

No matter what burn speed I set either K3B or the Gnome burning client at, my CDs will not burn successfully. It starts the burn, then after a few seconds it 'completes' the burn and then finishes with an error. Here is a link to the hardware I have:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827129007](http://www.newegg.com/Product/Product.aspx?Item=N82E16827129007)

Any help would be greatly appreciated!

Thanks,
Dan

---

### Post by taurus on 2007-05-19
What are you trying to burn anyway?

---

### Post by IgnacioMiller on 2007-05-19
.iso files and compilations of music are what I have tried so far.

---

### Post by IgnacioMiller on 2007-05-19
Here is the Debug Output of K3B:

```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-386
Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.23 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-111D'
Revision       : '1.23'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 705 KB/s
Track 01: data   682 MB        
Total size:      783 MB (77:36.00) = 349200 sectors
Lout start:      783 MB (77:38/00) = 349200 sectors
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
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 10646
Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  682 MB written.
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 3E 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.003s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 126976 bytes
Writing  time:   17.612s
Average write speed 563.4x.
Fixating...
Fixating time:   61.961s

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/hdc speed=4 -tao driveropts=burnfree -eject -data -tsize=349198s - 


```

---

### Post by IgnacioMiller on 2007-05-20
Bump!

---

### Post by archaggie828 on 2007-05-20
well, i had a problem even getting the red light to blink, but it's fixed. don't know exactly what i did that made it work, but i've had many successful burns. cd's and dvd's, writing and erasing.

---

