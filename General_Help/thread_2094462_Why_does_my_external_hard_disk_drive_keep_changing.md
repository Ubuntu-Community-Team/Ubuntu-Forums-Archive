---
title: "Why does my external hard disk drive keep changing mount points?"
date: 2012-12-13
forum: General Help
---

### Post by Welly Wu on 2012-12-13
I have an external Western Digital My Passport 2.00 TB USB 3.0 Portable  hard disk drive which I formatted using the /ext4 file system and I used  LUKS for full-disk encryption. It is mounted as /media/Data Drive 4 in  Nautilus. I have a System76 Lemur Ultra Thin (lemu4) notebook PC with  Ubuntu 12.10 64 bit GNU/Linux. Every time I shut down my System76 PC and  I reboot it, it changes the mount point for my WD portable hard disk  drive. Previously, it would mount it as /media/Data Drive 4_,  /media/Data Drive 41 and now it is currently mounted as /media/Data  Drive 42. This causes CrashPlan to do a data de-duplication from scratch  repeatedly.

Why is this happening?

How do I fix this problem so that it will mount as /media/Data Drive 4?

Please help me with detailed step-by-step instructions. Thank you.

---

### Post by Welly Wu on 2012-12-16
System76 replied to my help ticket and they told me to change the label for the WD hard disk drive using the Disks utility and reboot my PC. Then, I did that and it works now.

---

