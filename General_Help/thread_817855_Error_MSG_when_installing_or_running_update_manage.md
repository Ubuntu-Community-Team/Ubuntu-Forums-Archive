---
title: "Error MSG when installing or running update manager (ubuntu 8.04 hardy heron)"
date: 2008-06-04
forum: General Help
---

### Post by rated_emman on 2008-06-04
Hi! im runnin Ubuntu 8.04 Hardy Heron... and i get this msg when im installing something or running the update manager:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i tried to type the "dpke --configure -a" on the terminal but it gives me an error saying: 

dpkg: requested operation requires superuser privilege


and i am an administrator of the computer.. im the only user.... i am super new to this OS.. i've only used it for 5 days and still getting used to it... can anybody help me please? thanks a lot!

---

### Post by kostkon on 2008-06-04
You have to put sudo inj front of this command, i.e.:
```
sudo dpkg --configure -a
```
It will ask you for a password; just give your password since you are the first (and only) user of the system and thus you have admin priviledges.

---

