---
title: "While mounted /dev/sda wakes up the instant spin down command is sent"
date: 2023-03-30
forum: General Help
---

### Post by killwarez on 2023-03-30
I installed a new drive into headless Ubuntu 22.04 server today. Am trying to schedule the drive to spin down when not in use. The issue is that the drive wakes up less  than a second after being put to sleep:

```
[ 1490.067261] ata1.00: exception Emask 0x0 SAct 0x80000 SErr 0x0 action 0x6
[ 1490.067368] ata1.00: waking up from sleep
[ 1490.067430] ata1: hard resetting link
[ 1490.382868] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 1490.508708] ata1.00: configured for UDMA/133
[ 1490.508743] ata1: EH complete

```

If I unmount the drive, then spin down works.

**lsof** shows nothing associated  with /dev/sda or mount location.

I am issuing  spin down via hdparm. The drive is **WD8002PURP** and does not have APM support so I have to do spin downs manually. 

```

sudo hdparm -B 127 /dev/sda
 setting Advanced Power Management level to 0x7f (127)
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 04 53 40 7f 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 APM_level      = not supported

```


This worked on my previous drive (6TB WD Purple drive). How do I prevent the drive from waking up immediately after spinning down?

---

