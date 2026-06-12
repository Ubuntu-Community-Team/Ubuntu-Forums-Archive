---
title: "Boot to CLI via LiveCD?"
date: 2008-03-04
forum: General Help
---

### Post by altonbr on 2008-03-04
Is it possible to boot to a CLI via the Ubuntu LiveCD? I'm trying to copy data from a hard drive and I don't need a full blown GUI to mount then scp.

Knoppix isn't working on this computer. DSL is, but I can't use 'fdisk'.

Similar threads that state it is not possible (sort of):
[http://ubuntuforums.org/showthread.php?t=446455](http://ubuntuforums.org/showthread.php?t=446455)
[http://ubuntuforums.org/showthread.php?t=29195](http://ubuntuforums.org/showthread.php?t=29195)

---

### Post by jken146 on 2008-03-04
You could boot an Ubuntu live CD, let the GUI load, then press Ctrl+Alt+F1 to get to a virtual terminal.  Then you can shut down X: ```
sudo /etc/init.d/gdm stop
```
Then do whatever you want.

---

### Post by pawnrocket on 2008-06-18
How about creating a livecd that is only CLI? 

Install a cli 8.04 from the alternate installer and remastersys the system onto a cd? 
Is this possible?

---

