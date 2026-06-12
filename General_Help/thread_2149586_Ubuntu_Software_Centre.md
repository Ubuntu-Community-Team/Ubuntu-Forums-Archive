---
title: "Ubuntu Software Centre"
date: 2013-05-29
forum: General Help
---

### Post by Y^2om&amp;#7sgP on 2013-05-29
I've just re-installed Ubuntu 12.04 (was using Xubuntu) and added Cairo-dock.
I now find each time I try and access any program from the application menu on the dock, the Ubuntu Software Centre starts up.
It's getting to be a pain in the rear end
Is there a way to stop this happening?
Thanks all

---

### Post by ibjsb4 on 2013-05-29
Thats a strange problem.  Try removing or renaming the software- center configuration file in ~/.config

---

### Post by Y^2om&amp;#7sgP on 2013-05-29
I have deleted the file

softwarecenter.cfg

still same problem :(

---

### Post by ibjsb4 on 2013-05-29
Take it a step further, reinstall the software-center and reboot.

---

### Post by vasa1 on 2013-05-29
> **hattpa said:**
> I've just re-installed Ubuntu 12.04 (was using Xubuntu) and added Cairo-dock.
I now find each time I try and access any program from the application menu on the dock, the Ubuntu Software Centre starts up.
It's getting to be a pain in the rear end
Is there a way to stop this happening?
Thanks all
Sometimes, mimeapps.list can get corrupted: [http://ubuntuforums.org/showthread.php?t=1861067&p=11350914#post11350914](http://ubuntuforums.org/showthread.php?t=1861067&p=11350914#post11350914)

---

### Post by Y^2om&amp;#7sgP on 2013-05-29
Thanks for the suggestions guys.
Removing and re-installing software-center seems to have done the trick
It was a fresh install so no idea why this happened but is now fixed :D

---

### Post by ibjsb4 on 2013-05-29
Good deal :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

