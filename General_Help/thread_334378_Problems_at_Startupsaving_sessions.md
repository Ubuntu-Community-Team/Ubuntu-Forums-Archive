---
title: "Problems at Startup/saving sessions"
date: 2007-01-08
forum: General Help
---

### Post by PRGUY85 on 2007-01-08
Hey there:

I recently installed Edgy from scratch on my desktop computer.  I used Automatix 2 and followed the guide for Beryl with an ATI Radeon card.  Everything works fine, yet whenever I start up the system I don't get a window manager working (no Beryl nor metacity).  In order to get them, I have to go into a terminal and start them up manually.  I tried adding beryl-manager to startup programs but whenever I reboot, the program is not on the list as if it wasn't saving it. I have the system to save all session on shutdown as well...So what could it be?  Once I open a terminal and type beryl-manager but I would like to save this step by making the startup program list work.  As of now it is as if it doesn't allow programs to be added to the  list, or the sessions aren't saved even though the option is checked.

Any ideas?

---

### Post by yager on 2007-01-08
Check this thread for some help.  I had the same issue and it was a problem permission on one of the files.

[http://ubuntuforums.org/showthread.php?t=308648&highlight=startup+program+permission](http://ubuntuforums.org/showthread.php?t=308648&highlight=startup+program+permission)

Let us know how it works out.

---

### Post by taurus on 2007-01-08
Delete the **Default** session (System -> Sessions) and add whatever app you want to start to Startup Programs.

---

