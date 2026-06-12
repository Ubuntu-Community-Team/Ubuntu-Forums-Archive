---
title: "Basic Library Help"
date: 2008-03-28
forum: General Help
---

### Post by andrew_gatt on 2008-03-28
I'm writing some code based on sqlite, but i'd like to use some features of the new 3.5 series. The version in the repositories for Ubuntu 7.10 are 3.4.2 i believe. So i thought i'd just download the 3.5.7 tarball, configure, make, install. But i realised that a lot of other packages depend on the sqlite library, which i presume will break after i blast a new version over the top.

So what is the correct procedure to manually install an upgraded library? Install it too a different location? - But then how do i link to it properly without it becoming complicated?

Any thoughts on the matter would be well received.

Thanks
Andrew

---

### Post by justleen on 2008-03-28
IF the depencies are up-to-date, you can just install it on a different location. 

As in: if the new version of SQLite uses the same depencies your OK. 

i'd just try to build it from source, see what your missing.. (see if you get through the configure and make.. if so, install it..)

---

### Post by lloyd_b on 2008-03-28
> **andrew_gatt said:**
> I'm writing some code based on sqlite, but i'd like to use some features of the new 3.5 series. The version in the repositories for Ubuntu 7.10 are 3.4.2 i believe. So i thought i'd just download the 3.5.7 tarball, configure, make, install. But i realised that a lot of other packages depend on the sqlite library, which i presume will break after i blast a new version over the top.

So what is the correct procedure to manually install an upgraded library? Install it too a different location? - But then how do i link to it properly without it becoming complicated?

Any thoughts on the matter would be well received.

Thanks
Andrew

As a rule, "./configure --prefix=/usr/local" will override the default installation path, putting everything under the "/usr/local" tree rather than directly under the "/usr" tree.

Using this trick, you can install sqlite in "/usr/local", and when you want to compile against it specify "-L/usr/local/lib" so that it searches there first for libraries.

This should allow you to play with the new version, without screwing up anything that relies on the old version.

Lloyd B.

---

