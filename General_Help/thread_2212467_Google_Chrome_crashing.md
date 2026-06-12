---
title: "Google Chrome crashing"
date: 2014-03-21
forum: General Help
---

### Post by spanner2 on 2014-03-21
Hi there. The other day, the Chrome browser started crashing. After about 5 mins it becomes unresponsive, and sometimes Ubuntu (13.10) seizes up completely along with it (not every time, however, although Chrome always freezes). The exact same thing is happening with Chromium.

I've tried removing both (and purging them), but it hasn't helped. I've also tried selecting third party Radeon video drivers and disabling GPU in Chrome's settings, but these haven't helped either. I read about these potential solutions in other reports of Chrome becoming consistently unstable, by the way. 

I'm not very good with Ubuntu, as I'm new to it, so any help would be very much appreciated. Thanks in advance!

---

### Post by tgalati4 on 2014-03-21
What is the SMART status of your disk drive?

```
sudo smartctl -a /dev/sda
```

---

### Post by spanner2 on 2014-03-22
> **tgalati4 said:**
> What is the SMART status of your disk drive?

```
sudo smartctl -a /dev/sda
```

Hi there, thanks for replying. I installed smartools, ran the command you gave me and got the following info:

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue EIDE
Device Model:     WDC WD5000AAKB-00UKA0
Serial Number:    WD-WCAPW3284328
LU WWN Device Id: 5 0014ee 15586a58c
Firmware Version: 07.01N01
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7 (minor revision not indicated)
Local Time is:    Sat Mar 22 09:18:59 2014 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

---

