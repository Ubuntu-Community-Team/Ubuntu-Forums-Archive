---
title: "[apt-get] Permission before installing"
date: 2006-12-23
forum: General Help
---

### Post by navneeth on 2006-12-23
I though that this was enabled by default, but it doesn't seem so now, after a fresh install of Edgy. What do I do so that apt-get would ask me before installing [Y/n/?] ? 

Thanks.

---

### Post by gborzi on 2006-12-23
By default apt-get will ask for confirmation only in the case the required package needs the installation of other packages to satisfy dependancies. E.g. > gborzi@evo610:~$ sudo apt-get install abuse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  abuse-frabs
The following NEW packages will be installed:
  abuse abuse-frabs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3598kB of archives.
After unpacking 15.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

---

### Post by navneeth on 2006-12-23
Oh, ok. Thanks.

---

