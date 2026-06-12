---
title: "systemrescuecd question"
date: 2007-12-04
forum: General Help
---

### Post by thelugnut on 2007-12-04
Hello, 

I have three partitions: 
1.) sda1 for Windows XP formatted in ntfs, 
2.) sda2 for Ubuntu formatted in ext3, 
3.) sda3 for my data stuff formatted in fat32. 

The reason for this arrangement was both operating systems can read and write to the fat32 partition. 

I want to backup sda1, (Windows XP) using sda3 (data partition). 

Can I do this, or must they both be formatted the same? 

Thank you

---

### Post by KOld Iron on 2007-12-04
Hi,

I tried to do something similar (for some testing) a few days ago. Since you want to use the System Rescue CD, I would assume you want to image the XP partition. The only problem is, that FAT32 will only allow single files up to 4GBytes size (as I was reminded myself harshly) and I would think your XP partition has more data than that. So that is something to keep in mind.

On the other side, if you just want to copy the files, that should work, but then you will lose all XP-security information (again assuming you are copying from NTFS to FAT32), since FAT32 does not support that (apart from that I don't know, whether "cp" supports the transfer of this information to begin with).

So, in theory backing up data the way you describe it would work, but there are some other limiting factors providing some challenges.

---

