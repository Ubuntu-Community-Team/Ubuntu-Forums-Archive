---
title: "cpu 100% on copying files to usb pen drive"
date: 2007-01-09
forum: General Help
---

### Post by unikuser on 2007-01-09
When I am copying files to usb  pendrive, my cpu is at 100%. I noticed that drive cache is "write through" in my dmesg logs. How can I change that and will that affect copy speed in any way.

[17182001.664000] SCSI device sdb: 3964928 512-byte hdwr sectors (2030 MB)
[17182001.664000] sdb: Write Protect is off
[17182001.664000] sdb: Mode Sense: 03 00 00 00
[17182001.664000] sdb: assuming drive cache: write through

---

