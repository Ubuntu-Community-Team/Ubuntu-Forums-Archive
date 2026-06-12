---
title: "synaptic package manager error"
date: 2007-05-12
forum: General Help
---

### Post by wondermack on 2007-05-12
after opening my package manager:


[B]an error occured
the following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

so i went to the terminal, entered the given command, and it told me i needed superuser privilages.

please assist :(
IM aim, yahoo, or msn

---

### Post by taurus on 2007-05-12
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```
Post a complete error message if there is one.

---

