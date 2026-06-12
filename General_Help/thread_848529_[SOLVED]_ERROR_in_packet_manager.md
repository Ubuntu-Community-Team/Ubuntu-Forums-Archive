---
title: "[SOLVED] ERROR in packet manager"
date: 2008-07-03
forum: General Help
---

### Post by l0fls on 2008-07-03
every time i open packet manager i get the same problem
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


also when ever i got to update manager and try to update i get the same crap
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


the problems seem to be related help plz..

---

### Post by kellemes on 2008-07-03
Well? have you followed the advise?
From terminal..
```
sudo dpkg --configure -a
```

---

### Post by l0fls on 2008-07-03
Ty :) that did the trick

---

