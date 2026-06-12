---
title: "gfortran vs gfortran-10 vs gfortran-10-aarch64-linux-gnu"
date: 2022-08-23
forum: General Help
---

### Post by bigrockcrasher on 2022-08-23
So my question is broader then my example. I am going to install gfortran. Easy task . 
```
apt get install gfortran
```

I notice there are other versions of gfortran. I presume that when I install gfortran I get the newest version available in the standard repository's which in this case is gfortran-10.  Then I notice there are different versions designed for different architecture, which I always assumed that it picks the one for my architecture automatically which I am think I was wrong. I have a server with few intel xeon Gold 6240 processors. So, I can install the amd64 version. Can any one please explain the differences between these and the repercussions for installing the wrong one. Again this question is a bit broad because there are many packages that have these different options. I am hoping that there may be a little guide I can follow when I come across packages like this. 

thank you

---

### Post by dragonfly41 on 2022-08-23
An alternative .. just as reference ..

[https://reference.wolfram.com/language/ref/FortranForm.html](https://reference.wolfram.com/language/ref/FortranForm.html)

---

### Post by Holger_Gehrke on 2022-08-23
If you look at the package with 'apt show gfortran' you'll see the version it installs in the line that starts with 'Depends:'. 'gfortran' is an (almost) empty package which depends on a specific version of gfortran and some other things (cpp and gcc and their dependencies).
For the architecture there's an item you can put into the apt configuration named 'Architecture' which is the Architecture of the system (default: the architecture for which apt was compiled) and a second item 'Architectures' which is a list of all the architectures supported on the system.

Holger

---

