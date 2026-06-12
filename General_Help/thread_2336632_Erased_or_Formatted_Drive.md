---
title: "Erased or Formatted Drive"
date: 2016-09-09
forum: General Help
---

### Post by jackbn on 2016-09-09
I had a primary Ubuntu drive and a secondary data drive.
I used GParted to format a third drive, which it did, BUT the second drive was evidently erased.
How can the lost files on the erased drive be recovered?

I am (obviously) NOT an expert with Ubuntu, and will need detailed instructions.

Thanks

---

### Post by yancek on 2016-09-09
Do you mean partition or do you actually have three physical hard drives?  If you want to try to recover some of the files you can try going to the 'testdisk' site and downloading it.  There is a link to a step by step tutorial on the page.  You should always have backups before you modify partitions because there is always the potential for data loss.

---

### Post by jackbn on 2016-09-13
I had three physical drives in the computer -- a primary, a working secondary and a new tertiary.
When formatting the new drive, Gparted ALSO made the secondary inaccessible, or formatted it.

---

### Post by sudodus on 2016-09-13
I agree that ***testdisk*** is a good first choice, so try that. And it is a good idea to copy the drive (and use either the original drive or the copy as backup). If the drive is failing (physically), you should clone it as soon as possible and work on the copy, but this is not the case now.

You can copy your drive with ***ddrescue***, but be very careful, check and double-check, so that you are not overwriting more valuable data. The following link is addressing USB pendrives, but it is valid also for hard disk drives.

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

The next step, if testdisk fails to repair the file system, is ***photorec***. It can recover files without a file system, as long as the actual data on the drive surface is still there. Some data may be overwritten, but a lot of data remain, maybe most of it. Looking at signatures (typical patterns), photorec can identify data belonging to most files types for documents, photos, multimedia etc. It is a lot of hard work, but it is possible. Please find more details about testdisk and photorec at

[https://www.cgsecurity.org/](https://www.cgsecurity.org/)

---

### Post by jackbn on 2016-09-16
I guess my present problem is that the drive is not recognized, as a secondary drive. 
I did not install an OS, so of course it is not recognized as a primary drive.

Will the tools above find it?

---

### Post by oldfred on 2016-09-16
Does BIOS/UEFI show drive.
Unless BIOS shows drive, no operating system or software will see it.

Only if no operating system will it not be in boot list, but in BIOS it will show as part of all the hard drives.

What did testdisk show?

---

