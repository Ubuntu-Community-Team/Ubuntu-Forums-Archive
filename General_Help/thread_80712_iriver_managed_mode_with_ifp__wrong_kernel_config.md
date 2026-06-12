---
title: "iriver managed mode with ifp / wrong kernel config?"
date: 2005-10-22
forum: General Help
---

### Post by phen on 2005-10-22
hello!

i want to use my mp3 player iriver n10 in the manager mode thats the non-ums mode. if you ask why: i have to use it at least once to change its firmware to ums mode :-). i am not able to connect to my device.

the error output is: 
$ ifp ls
Device is busy.  (I was unable to claim its interface.)

i know that the ifp-line tool needs usbdevfs compiled into the kernel, but i dont know how to check my kernel config. i am using the standard breezy kernel. is there a list online with all modules/patches included? i don't want to install hundreds of mb of software to check whether i allready have usbdevfs or not.

thank you for help

---

### Post by hajk on 2005-10-23
You must have root privileges, so "sudo ifp ls" should give a directory listing on your iRiver (it does on mine with the standard Breezy kernel).

---

