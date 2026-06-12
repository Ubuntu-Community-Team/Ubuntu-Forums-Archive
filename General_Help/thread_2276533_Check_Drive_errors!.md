---
title: "Check Drive errors!"
date: 2015-05-03
forum: General Help
---

### Post by Yezinki on 2015-05-03
Is it possible to check HDD for errors using Ubuntu on a machine running W7?

Or do I have to install Ubuntu first?

What is the method, commands?

Thanks.

---

### Post by Yezinki on 2015-05-03
and yes just installed a new battery on this W7 lap.......any commands to check battery health and info?

Thanks again.

---

### Post by oldos2er on 2015-05-03
You need Linux tools to check Linux partitions, Windows can't see them much less repair them in any fashion. You could use any Ubuntu live medium or something more specialized like [SystemRescueCD]("http://www.sysresccd.org/Download"), boot from it to run checks or tests.

---

### Post by Mark Phelps on 2015-05-03
> Is it possible to check HDD for errors using Ubuntu on a machine running W7?

In W7, open File Explorer, right-click the "drive" you want to check, select Properties --> Error checking.  That will run CHKDSK against that partition and tell you the results.

If you want to check the entire physical drive, including unallocated space, you will need to download a disk checking utility from the drive manufacturer's website.  Those typically require MS Windows to run.

---

### Post by Yezinki on 2015-05-03
Wont it be easier if I install Ubuntu only, erase W7?

Will I be able to check the drive and battery vs. the System Rescue CD........or that bootable CD can check the drive thoroughly.

The reason for asking is that ran Dell Diagnostics and it reported corrupt  C partition......what does that mean?

Thanks.

---

### Post by Yezinki on 2015-05-03
> **Mark Phelps said:**
> In W7, open File Explorer, right-click the "drive" you want to check, select Properties --> Error checking.  That will run CHKDSK against that partition and tell you the results.

If you want to check the entire physical drive, including unallocated space, you will need to download a disk checking utility from the drive manufacturer's website.  Those typically require MS Windows to run.


Thanks

Ran CHDSK with chdsk/ r, but found none errors......don't know where does it store the log?

---

