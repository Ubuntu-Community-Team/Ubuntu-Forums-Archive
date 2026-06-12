---
title: "Help with apt-get"
date: 2006-11-22
forum: General Help
---

### Post by pranith on 2006-11-22
How do i use apt-get/dpkg or nethin to get the list of available (to install/upgrade) packages in a repository along with their info??:confused: .....like "yum" does it using "yum list available" or "yum info available" .....how can i achieve this using apt-utils ??:-k

---

### Post by gosh on 2006-11-22
Synaptic has the possibilities to see which repositories you have enabled and what packages are available.
Right click on a package to see the detailed info.

---

### Post by pranith on 2006-11-23
actually its like this......i want to write program to download all the available packages....for this i must know the list of packages rite....so how do i get this list from the repos thru apt-get or nethin.....i guess apt-get downloads the package lists first when we do 'apt-get update'....in wat format is the downloaded list and where is it...is it /var/cache/apt/pkgcache.bin ?? :-k wat is it ?:confused:

---

### Post by pranith on 2006-11-23
i think i got the answer.....from the cache we can get the info using "apt-cache dump" or "apt-cache dumpavail" ... :D :-D

---

