---
title: "Gparted error: Unable to read contents"
date: 2007-12-27
forum: General Help
---

### Post by firetree on 2007-12-27
I want to resize a NTFS partition.  However after unmounting, Gparted opens the folder of that partition and gives a warning massage on the partition: Unable to read the contents of this filesystem! Because of this some operations may be unavailable. What is the problem? What can I do?

---

### Post by Irihapeti on 2007-12-27
This happened to me once, quite a while ago. If I remember properly, I had Gparted installed on my computer and tried to use it from there. Even thought the NTFS partition wasn't mounted, GParted still didn't like it. Once I rebooted with the Gparted liveCD, it accessed the NTFS partition with no problems.

---

### Post by louieb on 2007-12-27
Gparted also checks NTFS partitions for errors. If it finds one  then it won't resize it. Does it dual boot? Boot to windows and run chkdisk.  
Before resizing an NTFS partition,  running chkdisk and disk clean up in windows  is always a good idea.

---

### Post by firetree on 2007-12-28
Thanks to all but chkdsk didn't solve.  However I used Paragon Partition Manager which solved my problem in Windows.

---

