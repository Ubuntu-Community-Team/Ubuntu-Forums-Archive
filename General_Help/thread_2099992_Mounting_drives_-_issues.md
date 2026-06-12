---
title: "Mounting drives - issues"
date: 2012-12-31
forum: General Help
---

### Post by archie456 on 2012-12-31
Hi,

I've eventually got my Ubuntu system running again after a problem with a SATA cable, and all seems well, except, I cannot mount one of my drives which I keep my stuff on.

In folder window, I see three devices in the top left, when I click on each an arrow appears next to it (which I assume means its mounted) and I can view the files.

The last drive, when I click on it, does nothing and then 'Unable to Mount Hard Disk' 'Operation was cancelled' appears. The hard disk then disappears from the list of devices on the left.

It only reappears when I reboot - and I get the same issue when I try to access it?

I used to be able to access this drive before I had the issue with the SATA cable.

Any advice?

Edit: I should add, the machine also has a Win7 install on a separate drive (not the one I can't mount) - If I boot to Windows 7, I can access the drive which I cannot mount in Ubuntu fine.)

---

### Post by vanadium on 2012-12-31
If this is a drive that is formatted in the ntfs file system (used by MS Windows), then connect the drive to a Windows system and have it checked using the disk repair tools of Windows.

---

### Post by Mark Phelps on 2012-12-31
You keep saying "drive" but I suspect that these are actually partitions -- all on a single, physical drive, right?

Since you can access that partition in Win7, next time you boot into it, open the Disk Management utility and look at the partition.  If it says Dynamic Disk next to it in the table at the top -- Linux can't use those types of partitions, but Win7 can.

---

### Post by Kirk Schnable on 2012-12-31
> **Mark Phelps said:**
> You keep saying "drive" but I suspect that these are actually partitions -- all on a single, physical drive, right?

Since you can access that partition in Win7, next time you boot into it, open the Disk Management utility and look at the partition.  If it says Dynamic Disk next to it in the table at the top -- Linux can't use those types of partitions, but Win7 can.
If you're not sure... you could post a screenshot of your disk manager, and we can assist you further with that information.

---

### Post by archie456 on 2013-01-01
Thanks for your help chaps - I booted into Windows 7 and CHKDSKed the disk and it found errors - which I assume is the problem.

I'll have to run some more checks on the disks to find out whats wrong with it.

---

### Post by vanadium on 2013-01-03
Linux will not automatically mount ntfs partitions that are "unclean". Once checked and repaired ith chkdisk, the parition will correctly mount under Ubuntu.

---

