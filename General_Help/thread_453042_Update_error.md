---
title: "Update error"
date: 2007-05-23
forum: General Help
---

### Post by Buggy on 2007-05-23
I'm running Feisty and when I try to update using the Update Manager I get an error msg.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What does this mean?  What is dpkg?

---

### Post by pbw on 2007-05-24
It means to run dpkg --configure -a (with sudo) to correct broken packages.

dpkg is the debian package management system.

---

### Post by joriad on 2007-05-24
This link will tell you about dpkg [http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)
as for 
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```
tells that the package install was somehow interrupted.
You can correct this in terminal, Applications > Accessories > Terminal
Then type 
```
sudo dpkg --configure -a
```

---

### Post by Buggy on 2007-05-24
Well that was easy!  Thanks guys.

---

