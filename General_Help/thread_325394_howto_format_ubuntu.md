---
title: "howto format ubuntu"
date: 2006-12-25
forum: General Help
---

### Post by elgorbadez on 2006-12-25
i have 2 harddrive. 1st one windows and 2nd is ubuntu. when i open the computer with windows i can't see the second harddrive(ubuntu).
how can i format my 2nd harddrive and use with windowsxp?
thanks

---

### Post by jasonlfunk on 2006-12-25
The formating the Linux uses (ext2 or ext3) is not natively supported in Windows, although there are some applications that claim to be able to read and write ext2 in Windows. Be careful with these though - some have the potential to screw up your disk. A simple Google search can find these. What I would recommend is that you create two partitions on one of the disks, format one with ext2 and install ubuntu on it and format the other one with FAT32 for the data that you want to share between linux and windows. Windows XP will automatically discover and mount the FAT32 partition.

---

