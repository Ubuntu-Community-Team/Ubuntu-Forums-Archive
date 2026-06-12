---
title: "synaptic package manager messed up"
date: 2007-08-23
forum: General Help
---

### Post by dannyr1992 on 2007-08-23
hey i just started the package manager up, and i got this error
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i tried doing what is said and i got this:
> dpkg --configure -a
dpkg: requested operation requires superuser privilege
danny@danny-desktop-linux:~$ 



please help, cheers

---

### Post by Steveway on 2007-08-23
Why don't you do what it says?
sudo dpkg --configure -a
You should have found this out in 2 seconds.

---

### Post by southernman on 2007-08-23
sudo dpkg --configure -a

---

