---
title: "GParted and FAT"
date: 2005-09-17
forum: General Help
---

### Post by moose6589 on 2005-09-17
Hello, 

I have been trying to resize my NTFS and FAT32 partitions using GParted to move 500 MB from the end of NTFS to FAT32. The NTFS resize seems to work, but the program won't let me change the FAT partition; it says it is unable to read the contents of this filesystem. I have already tried unmounting through /etc/fstab and restarting to no avail. Any ideas on why only the NTFS partition is readable and not the FAT partition? QTParted also does not work (but it has other problems as well).

---

