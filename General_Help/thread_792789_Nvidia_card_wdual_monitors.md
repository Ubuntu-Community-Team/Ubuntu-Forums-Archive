---
title: "Nvidia card w/dual monitors"
date: 2008-05-13
forum: General Help
---

### Post by tone33 on 2008-05-13
So I followed the advice on this post:

[http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)

and entered gksudo nvidia-settings in a terminal window but nothing happened.  I have installed the binary driver for my nvidia geforce 6600GT card via the packet manager.  Any ideas?

---

### Post by tone33 on 2008-05-13
Ah nevermind...  I had to install the settings package as well.

---

### Post by sethd32 on 2008-05-13
Glad to see you found the solution, but if anyone stumbles upon this thread looking for the same answer, you can install the settings manager with:

sudo apt-get install nvidia-settings

and ater that installs, run it by running the command

nvidia-settings

---

### Post by Zorael on 2008-05-13
You may want to tag the thread as solved to make the thread listing easier to parse by eye. You can do this in the Thread Tools dropdown menu.

---

