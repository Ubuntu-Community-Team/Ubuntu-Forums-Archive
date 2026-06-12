---
title: "Feisty: DVD burning disaster"
date: 2007-05-05
forum: General Help
---

### Post by junjan on 2007-05-05
Since I upgraded to Feisty I can not burn DVDs -It worked perfectly under Edgy-. CD burning is working properly though.

DVD -R are recognized by the system, but Gnomebaker or Nautilus ruin the DVDs; Brasero does not begin the work. 
DVD +R are not recognized by the system showing an "invalid mount option" error.

Any clue?

---

### Post by Buster222 on 2007-05-05
Is it a 32 or 64 bits system?

---

### Post by mdurham on 2007-05-05
never mind burning them, I can't even read them

---

### Post by junjan on 2007-05-06
> **Buster222 said:**
> Is it a 32 or 64 bits system?

32 bits here.

---

### Post by junjan on 2007-05-06
:-\"

Any Guru there to shred some light into this matter?

---

### Post by junjan on 2007-05-06
Maybe is it something to do with this bug??
[URL="https://bugs.launchpad.net/ubuntu/+source/udev/+bug/75753"]
Wrong group for IDE cdrom/cdwriter/dvd devices[/URL]

:confused:

---

### Post by junjan on 2007-05-12
This is the output of my DVD writer:

```
junjan@Junjan:~$ wodim -v -checkdrive dev=/dev/scd1
TOC Type: 1 = CD-ROM
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-4040B'
Revision       : 'A302'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000 (Reserved/Unknown)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 2097152 = 2048 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 3281 kB/s 18x CD 2x DVD

```

Is it ok? :confused:

---

### Post by junjan on 2007-05-28
Last kernel update has fixed the DVD-R issue. :D

DVD+R and +RW are still not recognized though. :(

---

### Post by mdurham on 2007-05-28
> **junjan said:**
> Last kernel update has fixed the DVD-R issue. :D

DVD+R and +RW are still not recognized though. :(
What kernel update? I haven't had one.

---

### Post by junjan on 2007-05-28
linux-generic 2.6.20.15.14 to 2.6.20.16.28.1 for me

---

### Post by junjan on 2007-11-03
I gave up all this story and waited for Gutsy to clear the whole issue. 

Unfortunately I continued having the same problem. No DVD burning whatsoever. I tried all the burning software around, gnomebaker, brasero, k3b, etc. I also tried many solutions coming from different forums, tested different kernels, change unit names and aliases, go through user-permissions discussions... No way.

Finally I gave up and kept using Windows for DVD burning until I discovered that Nero software existed for Linux. I installed version 3.0.0 waiting for a different error screen and suddenly it worked! Full recovery like in Dapper Drake times, 

No errors, full functionality. :)

GIve it a try if you have the same problem.

---

