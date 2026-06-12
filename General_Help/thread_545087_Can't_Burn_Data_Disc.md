---
title: "Can't Burn Data Disc"
date: 2007-09-07
forum: General Help
---

### Post by Spike-X on 2007-09-07
I'm unable to burn a data disc using GnomeBaker. When I try, I get the following:

```
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-110D'
Revision       : '1.17'
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
Speed set to 2822 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
wodim: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
Errno: 0 (Success), send_cue_sheet scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 20 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 26 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x26 Qual 0x00 (invalid field in parameter list) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 32
cmd finished after 0.014s timeout 200s
wodim: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
wodim: Cannot send CUE sheet.
wodim: Could not write Lead-in.
Writing  time:   14.914s
```

I get the same problem when I copy the data to an ISO image, then try to burn that. How can I fix this?

---

### Post by Spike-X on 2007-10-07
Never mind. Turns out my burner's knackered.

Thanks to everyone who replied, though!

---

