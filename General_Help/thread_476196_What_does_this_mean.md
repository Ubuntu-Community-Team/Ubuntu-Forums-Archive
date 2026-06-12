---
title: "What does this mean?"
date: 2007-06-16
forum: General Help
---

### Post by mancel on 2007-06-16
I've been experiencing freezing with feisty on my laptop.  When it freezes it's brief, maybe a minute being the longest.
When I look at /var/log/syslog after a freeze I get something like this:

```
Jun 16 23:45:06 izzy-lappy kernel: [29552.556000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jun 16 23:45:06 izzy-lappy kernel: [29552.556000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
Jun 16 23:45:06 izzy-lappy kernel: [29552.556000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jun 16 23:45:13 izzy-lappy kernel: [29559.560000] ata1: port is slow to respond, please be patient (Status 0xd0)
Jun 16 23:45:36 izzy-lappy kernel: [29582.576000] ata1: port failed to respond (30 secs, Status 0xd0)
Jun 16 23:45:36 izzy-lappy kernel: [29582.576000] ata1: soft resetting port
Jun 16 23:45:36 izzy-lappy kernel: [29582.928000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
Jun 16 23:45:36 izzy-lappy kernel: [29582.936000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
Jun 16 23:45:36 izzy-lappy kernel: [29582.936000] ata1.00: configured for UDMA/100
Jun 16 23:45:36 izzy-lappy kernel: [29583.116000] ata1.01: configured for UDMA/25
Jun 16 23:45:36 izzy-lappy kernel: [29583.116000] ata1: EH complete
Jun 16 23:45:36 izzy-lappy kernel: [29583.132000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
Jun 16 23:45:36 izzy-lappy kernel: [29583.148000] sda: Write Protect is off
Jun 16 23:45:36 izzy-lappy kernel: [29583.148000] sda: Mode Sense: 00 3a 00 00
Jun 16 23:45:36 izzy-lappy kernel: [29583.180000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 16 23:45:36 izzy-lappy kernel: [29583.188000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
Jun 16 23:45:37 izzy-lappy kernel: [29583.548000] sda: Write Protect is off
Jun 16 23:45:37 izzy-lappy kernel: [29583.548000] sda: Mode Sense: 00 3a 00 00
Jun 16 23:45:37 izzy-lappy kernel: [29583.568000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

What does this mean and how do I fix it?  It looks like the hdd. :/
thanks.

---

### Post by tgalati4 on 2007-06-17
Do you have an external USB drive connected?  What is the sda device that is called out in Feisty?  It appears that there may be a timing issue with the internal and presumably external harddrive.

You need to be specific about your hardware to get a more detailed answer.

---

### Post by mancel on 2007-06-17
Thanks for the help.
I was doing some more research last night and found that if you have a cd/dvd in the dvd drive it won't freeze up on you.  Another option is to crossflash the drive.
For the time being I'll probably just keep cd in there.  It works.
Thanks again for your reply.

---

### Post by Bluecube on 2007-07-23
I have this issue as well. I have a SATA HDD and DVD writer with two IDE HDDs. The issue only happened after a reinstall of Feisty and it's been driving me nuts. Most people who have this issue have their PC lock for 30secs. Mine locks for about 10mins... I've tried booting with no IDE drives attached to no avail. Apparently there's a bug in the Linux (not just Ubuntu) ATA drivers. There are a few fixes floating about but none seem to work for me. Hopefully a proper fix (rather than a workaround) will be made up soon as I'm having to use Vista just now and it's horrible!

---

### Post by Bluecube on 2007-07-24
Probably a bit too early to be 100% sure but I thought I'd let you know of a possible cure. If you go to Software Sources (Administration menu I think) and ensure that Feisty Backports is ticked before clicking on Update Manager then you can download the latest versions of the HAL. This has sorted my problem out. So far... Hopefully it won't re-occur.

---

