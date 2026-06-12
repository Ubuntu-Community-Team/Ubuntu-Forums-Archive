---
title: "Can't update my system"
date: 2007-02-23
forum: General Help
---

### Post by SirPaPa on 2007-02-23
Hello,  there's a problem with my system unable to update. 
I get the followihg error message. 
I like some help please. Thank,you so much.

---

### Post by bapoumba on 2007-02-23
Hello,
this usually means you have another package manager open (adept, aptitude ?). There is a lock file that allows only one package manager to run at a time.
If this is not the case, open a terminal (> Accessories > Terminal) and run:
```
sudo aptitude update
```
and report any error here.

---

