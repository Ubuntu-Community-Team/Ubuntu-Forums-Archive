---
title: "HDD formatted under Ubuntu will not work on windows PC"
date: 2013-08-04
forum: General Help
---

### Post by b3rylord on 2013-08-04
I recently used disk utility to format a USB drive to exchange large files between my Ubuntu 12.04 machine and two other Windows devices, one XP home and the other windows 7. I formatted it FAT. Neither of the two Windows machines would see it as a USB drive although they both acknowledged that "something" had been plugged in. Only by using Windows disc manager and reformatting FAT would they then see it as another usable drive. This Windows format took some 40 minutes whereas the Disk Utility format was over in seconds.
Once formatted by DU, the Ubuntu machine could read and write quite happily to the USB connected disc.

Any ideas what is going on here, as the FAT format selection in DU states, "A popular format compatible with almost any device or system, typically used for file exchange".  Is "almost" the key word here or should I have selected some other format/hidden option........confused I am......

---

### Post by Thee on 2013-08-04
Maybe you didn't unmount it after the format and it got corrupt. Or maybe the disk utility didn't do a good job. Who knows...
In any case, I recommend using GParted to format the drives.

---

### Post by Bashing-om on 2013-08-04
b3rylord; Hi !
Another consideration ...per MicroSoft indeed:
If this is a FAT32 filesystem, there is a 4GB limit on files being stored. You'll need to reformat to NTFS.
[http://support.microsoft.com/default...b;en-us;314463](http://support.microsoft.com/default...b;en-us;314463)

ubuntu happily reads and writes NTFS.

---

### Post by thespirit3 on 2013-08-05
Also, make sure the partition type is set correctly.  Linux doesn't care so much, you can set the partition type to Linux and format it NTFS.  I seem to recall windows being a bit more fussy about such things.

---

### Post by fdrake on 2013-08-05
use gparted (sudo apt-get install gparted) and creat a partition fat32. Now make sure you select the normal formatting not the quick one since you may not resolve the errors that you get,

---

