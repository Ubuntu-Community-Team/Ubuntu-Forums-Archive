---
title: "Strange Hal.dll Problem"
date: 2007-01-21
forum: General Help
---

### Post by DocHoliday52090 on 2007-01-21
I've encountered the famous Hal.dll error. 

I've seen all the posts about it on this site, but I still can't make it work. 

**:::**

Here's what I have according to the fdisk (?) command: (One Physical Drive)

Hda2 is a media storing NTFS partition. It holds boot.ini

Hda5 is where WinXP is installed. Also NTFS.

Hda4 is Ubuntu 6.10 

I don't remember what 1 and 4 where (or 0?) but they seemed to be part of Dell's recovery tools. I can check if it is needed. I'm currently using another computer, so I can't use Windows with that Computer to fix the boot.ini 

**:::**

What I've done:

Use Knoppix 5.1 Live! to go in and modify the boot.ini to change the partition(3) command to 2 and 5 (I thought the first would point to boot.ini and make it work, but it didn't. I used 5 once I realized that it probably wanted the location of Windows itself. This didn't work either.) and finally 6. I used six because I read Windows counts from 1, where Linux counts from 0. Therefore, to point it to Windows on hda5, I would have to change the value to partition(6) in both areas. 

It didn't work either. 

How can I resolve this problem?

---

### Post by DocHoliday52090 on 2007-01-22
Bump. 

Any ideas?

---

### Post by smittybilt on 2007-02-03
I apologize that someone hasn't gotten back to you sooner...

I had the exact same hal.dll problem with my Ubuntu and XP dual boot.  This thread helped me solve my problem.  (Specifically the post from **thomsuey**)  I followed his advice in the post and was able to boot back into XP.

[http://www.ubuntuforums.org/showthread.php?t=73254]("http://www.ubuntuforums.org/showthread.php?t=73254")


Hope this helps!!  :D

---

