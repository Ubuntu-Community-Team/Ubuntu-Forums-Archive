---
title: "drive permissions"
date: 2007-10-30
forum: General Help
---

### Post by Smokeyone on 2007-10-30
I have had endless troubles trying to make an audio cd which I have posted on the media forum. 
Exploring other avenues I have found that under Places/Computer CD-RW/DVD+-RW drive
properties/permissions - it says read only and I cannot change it. Could this be the cause of all my troubles and if so what next please !
Thanks

---

### Post by MrFSL on 2007-10-30
> which I have posted on the media forum. 
How about a reference link so we can better see what your problem is.

> t says read only and I cannot change it. Could this be the cause of all my troubles and if so what next please !
Not likely your problem. What applications have you tried? Have you tried the serpentine audio cd creator? If so what were your results/problems?

---

### Post by Smokeyone on 2007-10-30
gnomebaker reported this

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
atapi: 1
Device type : Removable CD-ROM
Version : 5
Response Format: 2
Capabilities : 
Vendor_info : 'PIONEER '
Identification : 'DVD-RW DVR-112D'
Revision : '1.06'
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
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size : 12582912 = 12288 KB
4Speed set to 705 KB/s
9 Blocks remaining: 181789
Starting to write CD/DVD at speed 4.0 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds. 4 seconds. 3 seconds. 2 seconds. 1 seconds. 0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB: 2A 00 00 00 09 99 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 09 99 0E 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 2457 (not valid)
__________________

---

