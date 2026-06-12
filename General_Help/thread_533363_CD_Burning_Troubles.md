---
title: "CD Burning Troubles"
date: 2007-08-23
forum: General Help
---

### Post by likemindead on 2007-08-23
I've searched quite a few threads to no avail. I can't seem to burn a CD. This is what GnomeBaker says:

```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MITSUMI '
Identification : 'CR-48X9TE       '
Revision       : '5.0E'
Device seems to be: Philips CDD-522.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1589248 = 1552 KB
FIFO size      : 12582912 = 12288 KB
dSpeed set to 4234 KB/s
 writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 158978
Starting to write CD/DVD at speed  24.0 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 16.992s timeout 60s
wodim: OPC failed.
Writing  time:   18.501s
```

And Serpentine simply tells me to try a different speed.

My CD-RW drive is a MITSUMI CR-48X9TE which I searched for in the forums and found nothing either. Please help? Thanks so much in advance. Blessings....

---

### Post by likemindead on 2007-08-24
:::Cough--bump--cough:::

No one?

---

### Post by strabes on 2007-08-24
Are you running gnomebaker as root?

---

### Post by likemindead on 2007-08-24
Uh... no. Isn't that generally advised against? I'm still awfully new to Linux.

I can burn with no problems on my Acer laptop in Feisty. Could my having both a CD-RW drive and a DVD-R drive on my desktop be part of the problem? Like how they're mounted, or something? By the way, the problem is on a HP Pavilion 522n with a Mitsumi CR-48X9TE and a LITEON DVD-ROM LTD 163. I've never changed any of the configurations. It's setup just as installed. Thanks again....

---

### Post by likemindead on 2007-10-01
Well, it's been quite awhile and still no help? I tried again and this is what I got this time:

```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MITSUMI '
Identification : 'CR-48X9TE       '
Revision       : '5.0E'
Device seems to be: Philips CDD-522.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1589248 = 1552 KB
FIFO size      : 12582912 = 12288 KB
 Speed set to 706 KB/s
(3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 98187
Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 02 6D 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 31.305s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 1460592 bytes
Writing  time:   54.910s
Average write speed  95.7x.
Fixating...
Fixating time:    0.016s

```

Any help? Please? Thanks in advance.... :confused:

---

