---
title: "how do i edit rc.local"
date: 2007-09-30
forum: General Help
---

### Post by feelthejoe on 2007-09-30
i have not been able to find info on here on how to edit rc.local.. im having problems with connecting to the internet with my new router for some reason i have to login to terminal and run..

poff dsl-provider
pon dsl-provider

to get the internet to work. i need to have it auto run this so my gf can use the computer when im not home.. from what i have read rc.local is the best option and type that above exit 0. but how do i edit and save changes to rc.local? thanks

---

### Post by Maestro23 on 2007-09-30
> gksudo gedit

*Opens up the text editor gedit with root privileges.  Make your changes and save.

---

### Post by quixotic-cynic on 2007-10-04
It is supposed to be at /etc/rc.local ...always helps to know the actual *location* of what you want to edit.

---

### Post by bodhi.zazen on 2007-10-04
> **Maestro23 said:**
> *Opens up the text editor gedit with root privileges.  Make your changes and save.

```
gksu gedit /etc/rc.local
```

---

