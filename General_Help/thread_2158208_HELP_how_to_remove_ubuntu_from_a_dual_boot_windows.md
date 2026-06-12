---
title: "HELP how to remove ubuntu from a dual boot windows 8"
date: 2013-06-28
forum: General Help
---

### Post by 2159clark on 2013-06-28
i put ubuntu on my computer last week give it half my hard drive only to find out i have no reason to use it. my windows 8 is alot easier for me as im only just getting to grips with computer.

last night i tried easyBCD that never work
ive only just bought my computer and i never got a boot cd with it so is there a way to remove ubuntu without one?
also i did play with the terminal in ubuntu last night but when it come to editing which os boots first it wouldnt type.

i have HBCD if that can be used at all

any help would be greatfull

---

### Post by Mark Phelps on 2013-06-28
You can create a Boot CD in Windows 8 by using the Recovery Drive option -- and it creates a disk, not a drive.

---

### Post by oldfred on 2013-06-28
From Windows make the repair flash drive.
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Then you can run this to uninstall Ubuntu. After that you can use the Windows Disk tools to resize the Windows NTFS partition.
      
 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by 2159clark on 2013-06-29
i cant find [OS-Uninstaller]("https://help.ubuntu.com/community/OS-Uninstaller") to download

---

### Post by 2159clark on 2013-06-29
/media/OS/ubuntu/uninstall-wubi.exe can  just use this?

---

