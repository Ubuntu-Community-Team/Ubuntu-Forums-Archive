---
title: "Force-enabling SMART on SATA devices"
date: 2017-07-24
forum: General Help
---

### Post by bcschmerker on 2017-07-24
I'm stumped on configuring SATA drives to enable SMART at all times; after startup, Disks reports "SMART is not enabled" on all four drives (viz., one Western Digital® WD1600JS and three Toshiba® MQ01ABD050) my rig.  The Phoenix® Award® BIOS Revision F6D on my Gigabyte® GA-MA78GM-S2HP has SMART enabled and SATA ports 0-3 using Intel® Advanced Host Controller Interface.  What needs be done to start SMART from the boot process on /dev/sda through /dev/sdd?

---

### Post by oldos2er on 2017-07-24
Try ```
sudo apt-get install smartmontools

sudo smartctl -s on /dev/sda
``` Substitude sdb etc. as needed for each disk.

---

### Post by bcschmerker on 2017-07-26
With smartmontools installed, the rig autoconfigured on boot!  All readings needed are accounted for.  Issue is RESOLVED FIXED.

---

