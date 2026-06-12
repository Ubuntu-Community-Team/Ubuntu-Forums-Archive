---
title: "Problems with permisions and wifi"
date: 2021-08-11
forum: General Help
---

### Post by marcsomic on 2021-08-11
Hi all,


I have Ubuntu 21.04 alongside Windows 10 installed and sometimes it gives me problems. Sometimes, when I boot Ubuntu as the first option I don't have access to the WIFI and I don't have the permissions to edit any content on my hard disk. This problem can be fixed by restarting my computer, booting Windows, resetting, and then booting as Ubuntu. I was wondering if anyone had this problem before or knows how to fix it properly.


Thanks in advance!

---

### Post by linerman on 2021-08-12
> **marcsomic said:**
>  I don't have the permissions to edit any content on my hard disk. 

I assume you have Fast Boot and/or Hibernation option enabled in Windows.
Turn FastBoot off.
Or if you do not want to do that and still want to have access to your NTFS drives in Ubuntu, make steps:
1. Do not reboot Windows, only do proper shutdown with ...-> (look pt.2)
2. Press and hold Left Shift during clicking Shutdown system in Windows. Hold it till the computer switch off.
3. Ubuntu should have now access to your NTFS disks, but be careful with messing with Windows system files and folders during Ubuntu session.

---

