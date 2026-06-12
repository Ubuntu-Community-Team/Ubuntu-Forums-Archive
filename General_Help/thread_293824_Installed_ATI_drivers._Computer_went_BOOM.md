---
title: "Installed ATI drivers. Computer went BOOM"
date: 2006-11-05
forum: General Help
---

### Post by krazed nun on 2006-11-05
hey, i am running the live CD right now. Anyways,  i decided i would install the official ATI drivers from the official ATI site for my graphics card (ATI mobility radean 9200). After i installed it as root, it said there was an error. I read the log. It said something that it couldn't do something with a module. After that, i rebooted and i couldn't get a display after everything loaded. IT went straight to a terminal like screen. AND, it said something was wrong with the the graphical interface. Please help.:)

---

### Post by NeoLithium on 2006-11-05
When you get to the graphical interface, try 
```
 sudo dpkg-reconfigure xserver-xorg 
```
And follow that through, you should be able to get yourself back up and running.

---

