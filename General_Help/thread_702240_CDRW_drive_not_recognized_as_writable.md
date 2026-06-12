---
title: "CDRW drive not recognized as writable"
date: 2008-02-20
forum: General Help
---

### Post by asaz989 on 2008-02-20
My CD drive is recognized for the purposes of reading, but it turns out that, in the hardware recognition, it's only recognized as cdr and dvdr, NOT as cdrw (which it is). In particular, in Device Manager the storage.cdrom.cdrw flag is FALSE, storage.cdrom.write_speed is 0, and storage.drive_type is cdrom.

How do I get Gutsy to recognize the hardware as CDRW?

---

### Post by blueturtl on 2008-02-20
Have you tried to actually burn a CD-RW disc with the drive?

The labels are often wrong and in a lot of configuration settings the speed setting 0 actually means "the highest speed a drive can go".

---

### Post by asaz989 on 2008-02-20
Yes, I have - Nautilus CD Burner does not recognize that there is a CD burner attached and only gives me the "Write Image to File" option, and inserting a blank CD does not bring up the CD burner window as it should, but rather just leaves an icon sitting there in Nautilus saying "Blank CD".

---

### Post by asaz989 on 2008-02-20
Just installed GnomeBaker to see if that would work, and got an error message which I hope will be useful:

```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-ROM UJDA775 '
Revision       : 'DA03'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0008 (CD-ROM)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0008 (CD-ROM) (current)
wodim: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.

```

---

