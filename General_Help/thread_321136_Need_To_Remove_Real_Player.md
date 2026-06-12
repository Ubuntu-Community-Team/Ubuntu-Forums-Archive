---
title: "Need To Remove Real Player"
date: 2006-12-18
forum: General Help
---

### Post by Mark76 on 2006-12-18
And all associated files so that I can reinstall it in the hope that it'll work properly the second time around.

What do I need to do?

---

### Post by endersshadow on 2006-12-18
```
sudo apt-get autoremove --purge realplayer
sudo apt-get install realplayer
```

Voila :-D

---

### Post by Mark76 on 2006-12-18
Autoremove is an invalid operation? :?

---

### Post by hanzomon4 on 2006-12-18
```
sudo aptitude purge realplayer
```

---

### Post by Mark76 on 2006-12-20
It didn't work :(

---

### Post by Mark76 on 2006-12-20
I wonder if the Firefox and Opera plugins for RP might be at fault? :-?

---

### Post by Azakus on 2006-12-20
```
sudo aptitude --purge remove realplayer
```

---

### Post by Mark76 on 2006-12-20
mark-williams@cpc1-nfds11-0-0-cust975williams:~$ sudo aptitude --purge remove realplayer
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
mark-williams@cpc1-nfds11-0-0-cust975williams:~$

---

### Post by Azakus on 2006-12-20
Did you install realplayer from Automatix? If you did, uninstall it from Automatix

---

### Post by Mark76 on 2006-12-20
And how do I do that?

---

