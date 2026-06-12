---
title: "Complications"
date: 2006-11-01
forum: General Help
---

### Post by glaeven on 2006-11-01
Ok, I have posted here a couple times before, mainly about my wireless USB adapter. It all fixed in Edgy.

Ok, i decided to add some programs. i used the add/remove tool in the application menu. i selected a bunch and hit apply. it downloaded some, then said it was out of disk space. it continued to download, and started installing. then it finished and came up with a bunch of errors. The update icon appeared in notification area and it said i needed to run synaptic to fix broken packages. i did and evertime i try to fix it i get this:

E: libmono-sqlite2.0-cil: Package is in a very bad inconsistent state - you should

sometimes, it comes up and tells me to run "dpkg --configure -a"

that does nothing. please help

---

### Post by glaeven on 2006-11-01
nevermind. "sudo apt-get check -f" fixed it all.

---

