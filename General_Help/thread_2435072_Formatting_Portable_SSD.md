---
title: "Formatting Portable SSD"
date: 2020-01-15
forum: General Help
---

### Post by brenneke on 2020-01-15
I have purchased two Lexar portable SSDs but cannot mount them. Could you please give me advice on what would be proper way to format for use on both Ubuntu and Windows?
Also, what is unallocated partition all about?



[ATTACH=CONFIG]284804[/ATTACH]

---

### Post by Impavidus on 2020-01-16
It's formatted as exfat, but there is a problem with it, so it can't be mounted. As the disk is new, you can just format it. For compatibility with both Windows and Linux, use ntfs. You'll need Windows tools for the occasional filesystem check.

The unallocated part is the part of the hard drive that's not part of any partition.

---

### Post by HermanAB on 2020-01-16
+1 for NTFS.

NTFS is a journaled file system which ensures that your data will not get corrupted when the disk is unplugged.

The NTFS Linux driver is good enough for general use.  If you do get errors, fix them with Windows tools.

---

### Post by oldfred on 2020-01-16
+1 on NTFS

The exFAT format is proprietary to Microsoft.
But there is a reverse engineered driver in Ubuntu. 
sudo apt-get update && sudo apt-get install exfat-utils

---

### Post by yancek on 2020-01-16
Most Linux systems do not have the software installed by default to use/access exfat filesystems and I don't believe Ubuntu does either. ntfs is of course supported as indicated above.  You could also create a partition ntfs for windows and extr or other Linux fileysystem for your Linux.  Depends upon what you intend to do with the data.

---

### Post by brenneke on 2020-01-16
[QUOTE=The unallocated part is the part of the hard drive that's not part of any partition.[/QUOTE]

Yes, but why is it there and what is it's purpose?

---

### Post by brenneke on 2020-01-16
I am using for backup only.  Formatted to NTFS using Disks, working perfectly now - thanks all for replies.

---

### Post by dragonfly41 on 2020-01-16
I recently purchased an external SSD and I learned from reading various articles that the SSD requires about 10% of the total space (or more) to be left "unallocated". Apparently this increases the life of the SSD. Search "SSD provisioning".

---

### Post by Impavidus on 2020-01-16
The unallocated space is only 0.0007 percent of the drive. That's not enough to make a difference to anything. It probably happened for alignment reasons or some rounding somewhere.

---

