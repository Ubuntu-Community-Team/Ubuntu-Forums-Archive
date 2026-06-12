---
title: "Have to fsck read-only hard drive very frequently"
date: 2022-02-16
forum: General Help
---

### Post by uacnt83982803 on 2022-02-16
I am having my hard drive become read-only very often (as in, nearly daily) after, and only after, the screen locks (based on whatever time I set it).  The system is not suspending.

It will run day after day without any issue if I disable screen lock, but after about 3 screen locks, it then requires a reboot, falls into initramfs errors (always at the same spot: /dev/mapper/ubuntu--vg-root) and after fsck'ing it and fixing all of the errors, it's fine.

I have done extensive testing of the hard drive, and extensive research online regarding the SMART statistics.  The bad spots (very few) never change, never increase, and the drive health is Good.

The problem seems to creep up as swap space grows.  I understand that Ubuntu prefers to use swap space if it's available, even if it doesn't really need it.  I don't know if this has anything to do with the problem.

What is causing this?  It's to the point where this system is practically unusable.

---

### Post by TheFu on 2022-02-16
If it is an SSD, it is failing. Soon it won't allow reads at all. Replace ASAP ... you have a week or so, best case.

If it is a HDD, use badblocks to mark the locations of the  ... er ... bad blocks, so those are never, ever used.  If there are more than 10, I'd pull that disk from all production use.

If the file systems are ext2/3/4, we can run **tune2fs** to force an fsck at whatever interval you choose.  I think the defaults are 30 reboots, which for my systems could be over 4 yrs, so I changed it to be 60 days.

SMART reporting "Good" is next to useless.  There are about 10-15 useful SMART attributes which try to warn us of a failing disk in advance, but we need to pay attention.  Even if we are paying attention, backblaze's quarterly drive failure statistics say that 28% of the time, no clear SMART data issues are seen before a drive fails.

Be certain you have good backups and can restore those. Nothing replaces good backups.

---

### Post by HermanAB on 2022-02-17
Most desktop machine trouble is caused by bad power quality - consider getting a half decent UPS.  The reason laptop machines are so popular, is because they have a built-in battery which prevents most issues.

---

### Post by uacnt83982803 on 2022-02-17
It's on a Schneider UPS, so I don't think that's it.  

To TheFu, thanks for the detailed info.  Agreed backups are critical, and I have everything very recently backed up to multiple locations both local and in the cloud.

I think it's time to replace the drive.  Looking at a Crucial MX500 1TB SATA 2.5 inch drive.  Any reason that wouldn't work with Ubuntu?
[h=1][/h]

---

