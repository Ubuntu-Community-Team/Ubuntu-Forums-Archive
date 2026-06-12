---
title: "exFat/NTFS problems - FUSE related?"
date: 2013-08-07
forum: General Help
---

### Post by Gitfinger on 2013-08-07
For some time I've been trying to format an external hard disk with either exFat or NTFS for large file support and so it can be easily accessed from Windows/Mac.

The main purpose of the external drive is for backup. After creating either file system with mkfs I would then run a backup using rsync (it's a file based backup only) that should copy about 500GB of data. No matter how many times I tried the copy would eventually fail. The first symptom would be the system would become unresponsive and I'd lose communication over ssh. This would eventually require a cold reboot of the system.

During the backup I would run df -h and you could see several hundred GBs of data had been copied. However when the system crashed and I reconnected and remounted the drive there was barely 100MB showing as being copied. fsck would seem to show that the file system had no errors, including mounting the disk on Mac OS X and checking there. It seemed almost regardless of whether it was NTFS or exFat (anything to do with Fuse really) I would experience the same symptoms. Creating a Ext4 or Fat32 (anything not using Fuse) the rsync would be fine.

Has anyone experienced this or have any suggestions as to the cause of the problem please?

---

