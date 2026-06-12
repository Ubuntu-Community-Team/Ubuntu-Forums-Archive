---
title: "gdebi/gksu fails when installing packages."
date: 2014-04-21
forum: General Help
---

### Post by cdysthe on 2014-04-21
Hi,

I use gdebi to install debs on Ubuntu which again uses gksu for root access. However, lately I am not able to install anything with gdebi since gksu fails with:

** (gksu:3290): CRITICAL **: fcntl error
** (gksu:3290): WARNING **: Lock taken by pid: -1. Exiting.

If I sudo gdebi in the first place packages are installed without problems, but as soon as gksu is called I get this error and the package isn't installed. I also have problems with other applications using gksu. 

Is this a bug in gksu or is something else wrong?

---

