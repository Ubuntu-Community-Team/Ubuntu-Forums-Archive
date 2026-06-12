---
title: "Stuck at Grub rescue screen after factory resetting ubuntu installed laptop."
date: 2014-08-12
forum: General Help
---

### Post by GurbrinderSingh on 2014-08-12
case study:
i have a notebook with preinstalled win 7 on it. I installed ubuntu 12.04 on it a year ago. Dual boot worked just fine. But after few months hard disk got some problem and when i tried to boot in windows 7 environment it started showing the error that it can't boot the os due to HD bad sectors. I sticked to ubuntu till now as ubuntu worked just fine till yesterday. So i  used Sony vaio recovery tools and reset it to factory settings from the recovery drive already available in it. It recreated the partitions to the factory settings. But when i rebooted it is showing error

"
error: no such partition
grub rescue>
"
i don't know what to do?


WHATS MAJOR PROBLEM?

i can't Access BIOS settings bcz its corrupted 6 months ago. And i can't boot from any CD/DVD or USB to fix the error.

---

### Post by GurbrinderSingh on 2014-08-12
O God! No reply? There is no answer to this question? Or there are no volunteers to help?

---

### Post by mörgæs on 2014-08-12
Bumping after one hour is impolite and not likely to give you friends. Please notice that I already jailed one of your bumps. 

Please wait 24 hours. Patience!

---

### Post by Mark Phelps on 2014-08-12
It's likely the factory restore did not affect the MBR -- where it is STILL pointing to GRUB from the earlier install.  You need to restore Win7 boot capability before you reinstall Ubuntu.

To do that, you need to be willing to purchase a Win7 Repair ISO to make that repair CD -- which you could have done for free, when Win7 was still working.

If you have access to a working PC and a CD burner, then visit the linked site and purchase the ISO image:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Once you have that CD burned, boot from it and run Win7 startup repair three times -- that's right, three times.

Once that is working OK, you will then need to reinstall Ubuntu.

---

