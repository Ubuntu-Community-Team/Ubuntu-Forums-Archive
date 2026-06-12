---
title: "Rpm Database"
date: 2007-03-13
forum: General Help
---

### Post by bindigi01 on 2007-03-13
Hey guys 
i am installing oracle 10g in Edgy and i have passed the oracle pre checks  
the problem is the installatin stopps  because it can read the index of rpm data base from /var/lib/rpm i have installed rpm in may system and initiated rpm db using 
rpm -initdb
and rebuld it many tims 
rpm --rebulddb
the error is
cannot read index using db3 bad file descriptor  

HOW i can make rpm acts will in Ubuntu?

---

### Post by zvacet on 2007-03-13
```
sudo alien file_name rpm
```
Chek first in synaptic that you have alien installed.If you do run upper command and your rpm files will be converted in deb files.

---

### Post by bindigi01 on 2007-03-13
thank u for replying but not that what i need 
i need rpm to creat a proper db of packs to oracle see it and use it

---

### Post by zvacet on 2007-03-14
Well,maybe I missunderstand you.but I´m 100% sure that you can not run rpm in Ubuntu without convert it to deb.

---

