---
title: "upgrade - packages have been kept back"
date: 2016-09-23
forum: General Help
---

### Post by marchello_lippi2 on 2016-09-23
Hi all, 

How do I solve the below? 

```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ubuntu-core-launcher vim vim-common vim-runtime vim-tiny
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

```

---

### Post by kc1di on 2016-09-23
This happens when there is a situation that upgrading the package will cause a package to either be removed of a new package to be installed that was not installed already.

here is a web page that explains how to get around that.  
some may advise you to do a dist-upgrade but this can be dangerous to a stable system.   It will install all the kept back packages but may also remove or install new packages that could break your system.  
anyway here's the page:
[http://unix.stackexchange.com/questions/38837/what-does-the-following-packages-have-been-kept-back-mean]("http://unix.stackexchange.com/questions/38837/what-does-the-following-packages-have-been-kept-back-mean")

---

