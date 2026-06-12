---
title: "View Windows C dive through Ubuntu LiveCD."
date: 2007-03-04
forum: General Help
---

### Post by BlkMagik07 on 2007-03-04
Hey, sadly I partially went back to Windows (on a partition) because Ubuntu was a pain to set up.  I just want to know how do I view the C drive to put an .exe file into there so when I log into Windows I can retrieve it (basically transfer files from Ubuntu to Windows and vice versa) without burning a CD or using a flash drive.  The reason I'm asking is because Windows doesn't have the drivers for my Network Card but Ubuntu is using the card just fine so I downloaded the driver installer in Ubuntu.

---

### Post by taurus on 2007-03-04
If your Windows is using ntfs filesystem, then you need to install ntfs-3g driver before you can write to it.  There is nothing around it unless you use a floppy, thumbdrive, or a CD.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

And of course, you can view Ubuntu (ext2/ext3) fine from Windows if you use [http://www.fs-driver.org](http://www.fs-driver.org).

---

