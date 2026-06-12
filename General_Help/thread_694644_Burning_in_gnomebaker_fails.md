---
title: "Burning in gnomebaker fails"
date: 2008-02-12
forum: General Help
---

### Post by mathewc on 2008-02-12
Hello Gents,

I'm having a problem burning anything. I've tried running gnomebaker as root and still have the same issue.

I'm running gutsy on a Dell Vostro 200

Here is the output on the console: 

mathew@Unbutube:~/sudo gnomebaker 
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Here is the output in the app:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
scsidev: '2,0,0'
scsibus: 2 target: 0 lun: 0
Linux sg driver version: 3.5.34
SCSI buffer size: 64512
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 Jörg Schilling
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'schily-0.9'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identifikation : 'DVD+-RW TS-H653B'
Revision       : 'D200'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: CD-R
Profile: DVD-R/DL sequential recording 
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R (current)
Profile: CD-ROM 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: 
Drive buf size : 1962752 = 1916 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Drive does not support TAO recording.
cdrecord: Illegal write mode for this drive.

---

### Post by apetresc on 2008-02-12
The problem seems to be that you're trying to burn in TAO mode (Track-At-Once), which either your CD-R's or your burner does not seem to support. Switch to DAO (Disk-At-Once) mode and try that.

If your client doesn't mention "DAO" or "TAO", they probably call it "Multisession" or something like that. Make sure Multisession is turned *off*.

Hope this helps.

---

