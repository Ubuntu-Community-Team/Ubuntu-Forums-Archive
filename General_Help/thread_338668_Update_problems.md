---
title: "Update problems"
date: 2007-01-14
forum: General Help
---

### Post by NumberOne on 2007-01-14
I'm having a small problem.  The were several updates to be installed about 3 days ago (about 50 +) and all updated with no errors.  However, this on file "libevas1-loaders-all"  is sill in the update notification area.  I have installed it 5 times but it never leaves the update notification.  Each time I install it it completes successfully with no errors, It just won't go away.

I am running 6.10 server with the ubuntu desktop.

Any thoughts???

---

### Post by kingmonkey on 2007-01-14
Try using

```
sudo apt-get dist-upgrade 
```

---

### Post by Sef on 2007-01-14
It could be being held back for some reason.   I have 2 packages now like that.

> sef@jokat1:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libggi2 mplayer
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


You just have to wait until they are no longer held back then they will upgrade.

---

