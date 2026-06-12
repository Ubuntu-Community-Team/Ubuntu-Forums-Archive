---
title: "Wodim won't write to dvd-ram"
date: 2019-01-23
forum: General Help
---

### Post by Colin@oxford on 2019-01-23
I have a blank (unused) dvd-ram (it happens to be one I had lying around) that I want to put an ISO file on.

K3B says "no medium information" so I tried wodim, which looks hopeful.  This is output using -prcap:
```

$ wodim -prcap -dev=/dev/sg1
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ASUS    '
Identification : 'DRW-24F1ST   a  '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.

Drive capabilities, per MMC-3 page 2A:

  Does read CD-R media
  Does write CD-R media
  Does read CD-RW media
  Does write CD-RW media
  Does read DVD-ROM media
  Does read DVD-R media
  Does write DVD-R media
  Does read DVD-RAM media
  Does write DVD-RAM media
  Does support test writing

  Does read Mode 2 Form 1 blocks
  Does read Mode 2 Form 2 blocks
  Does read digital audio blocks
  Does restart non-streamed digital audio reads accurately
  Does support Buffer-Underrun-Free recording
  Does read multi-session CDs
  Does read fixed-packet CD media using Method 2
  Does not read CD bar code
  Does read R-W subcode information
  Does return R-W subcode de-interleaved and error-corrected
  Does read raw P-W subcode data from lead in
  Does return CD media catalog number
  Does return CD ISRC information
  Does support C2 error pointers
  Does not deliver composite A/V data

  Does play audio CDs
  Number of volume control levels: 256
  Does support individual volume control setting for each channel
  Does support independent mute setting for each channel
  Does not support digital output on port 1
  Does not support digital output on port 2

  Loading mechanism type: tray
  Does support ejection of CD via START/STOP command
  Does not lock media on power up via prevent jumper
  Does allow media to be locked in the drive via PREVENT/ALLOW command
  Is not currently in a media-locked state
  Does not support changing side of disk
  Does not have load-empty-slot-in-changer feature
  Does not support Individual Disk Present feature

  Maximum read  speed:  8468 kB/s (CD  48x, DVD  6x)
  Current read  speed:  8468 kB/s (CD  48x, DVD  6x)
  Maximum write speed:  8468 kB/s (CD  48x, DVD  6x)
  Current write speed:  8468 kB/s (CD  48x, DVD  6x)
  Rotational control selected: CLV/PCAV
  Buffer size in KB: 768
  Copy management revision supported: 1
  Number of supported write speeds: 0

Supported CD-RW media types according to MMC-4 feature 0x37:
  Does not write multi speed       CD-RW media
  Does not write high  speed       CD-RW media
  Does not write ultra high speed  CD-RW media
  Does not write ultra high speed+ CD-RW media

```

I then tried writing the ISO file:
```
$  wodim -v dev=/dev/sg1 -eject <isofile>
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '/dev/sg1'
devname: '/dev/sg1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.36
Wodim version: 1.1.11
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ASUS    '
Identification : 'DRW-24F1ST   a  '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0012 (DVD-RAM)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) (current)
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
wodim: Found unsupported DVD-RAM media.
wodim: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
Using generic SCSI-3/mmc   CD-ROM driver (mmc_cd).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 456704 = 446 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data  1367 MB        
Total size:     1570 MB (155:38.48) = 700386 sectors
Lout start:     1571 MB (155:40/36) = 700386 sectors
Current Secsize: 2048
wodim: Unspecified command not implemented for this drive.
wodim: WARNING: Could not manage to find medium size, and more than 90 mins of data.
Speed set to 4155 KB/s
Starting to write CD/DVD at speed  23.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
wodim: Unspecified command not implemented for this drive.
wodim: Cannot get next writable address.
Writing  time:    0.006s
Average write speed 999.0x.
Fixating...
Fixating time:    0.000s
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

```

So the prcap says that it does support dvd-ram, but when writing it says that it doesn't.

What does "Unspecified command not implemented for this drive." mean?

Any suggestions to get round the problem?

---

