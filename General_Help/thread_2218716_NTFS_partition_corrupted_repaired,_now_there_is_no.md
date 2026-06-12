---
title: "NTFS partition corrupted: repaired, now there is no data"
date: 2014-04-21
forum: General Help
---

### Post by Marco_Antonio_Ro on 2014-04-21
Hello,
In my "dual boot pc", I have a partition that has been identified by UBUNTU as "corrupted"
I have returnet to Windows and tried to repair it, but it showed that it was necessary to "unmount" the partition before attempting to do repair, I accepted but nothing happended, the 3 times i tried it.
I then came back to UBUNTU, and the partition mounted without errors, but now it apperars no data in it.
I have tried ntfsfix but the partition appears as a healthy partition, empty

Thanks for your valuable help!
Best regards

SYSTEM INFORMATION:
Dual Boot:
WINDOWS 7 ULTIMATE (NTFS)
UBUNTU 12.04 LT 64-bit (ext4)
Kernel: 3.8.0.38-generic
GNOME 3.4.2

DATA PARTITION: NTFS

HARDWARE:
RAM: 1.9GB
CPU: Intel Core 2 DUO CPU T7300 @ 2.00GHz x 2

---

### Post by monkeybrain20122 on 2014-04-21
How do you repair Linux file system is Windows?? ntfsfix by its name repairs ntfs and Ubuntu should be installed in ext4. ntfs is a MircoSoft file system.

---

### Post by Marco_Antonio_Ro on 2014-04-21
My UBUNTU system is installed in an ext4 partition, windows is installed in an NTFS one... and there is A THIRD partition: an NTFS, where I put the data to shar between the two systems.
After working with windows, I restartd with the UBUNTU partition, and the data (ntfs) partition was corrupted.

---

### Post by Mark Phelps on 2014-04-21
The ntfsfix app only repairs trivial errors in Windows filesystems.  Unfortunately, it is NOT a substitute for Windows CHKDSK.

If you want to try repairing the partition with a Windows partitioning tool, download and burn a CD of the Minitool Partition Wizard Boot CD, boot from that, and select the Check function.  That will run CHKDSK on the partition.

If that does not work, you are looking at using Windows data recovery apps to get files and folders back -- and the good ones are not free.

---

### Post by Marco_Antonio_Ro on 2014-04-22
Is there any other solution in UBUNTU to "reconstruct" the partition?

---

### Post by dragonfly41 on 2014-04-22
try testdisk which is in the Ubuntu software centre

read the full step-by-step guide to usage.

---

### Post by Marco_Antonio_Ro on 2014-04-23
> **dragonfly41 said:**
> try testdisk which is in the Ubuntu software centre

read the full step-by-step guide to usage.
Thanks, I will take a look at it!

---

