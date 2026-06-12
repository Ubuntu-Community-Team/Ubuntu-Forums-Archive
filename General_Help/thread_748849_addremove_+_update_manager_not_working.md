---
title: "add/remove + update manager not working"
date: 2008-04-07
forum: General Help
---

### Post by novabobogun on 2008-04-07
So basically I installed Ubuntu 7.10 yesterday. I ran some updates, and everything went fine. Next I went to add/remove and downloaded aMSN, everything went well. The next day I  tried running some of the remaining updates, the normal window popped up and started searching for updates, an error message appeared when I pressed the "install" button: [B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B]

Next I tried add/remove everything went fine, when I selected a package and pressing apply changes the same error message appeared. This time I actually tried the instructions stated in the message by opening a terminal (I'm not completely new to Linux), I think 3 processes started and ended, when it got to the 4th process, it took a little longer, I presumed it was blocked so I closed the terminal... Sometime later I repeated the process, instead of 3 processes there was only one, the one that was blocked.
Please respond as soon as possible.

:KS I think it's important to know that I've had the same problem with my past system, Fedora Core 5 :KS

---

### Post by SOULRiDER on 2008-04-07
Try doing
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude dist-upgrade
```

Even if it seems locked, wait a bit.

---

### Post by novabobogun on 2008-04-08
Thanks for the help, but do I run those commands even if the process starts?:confused:

---

