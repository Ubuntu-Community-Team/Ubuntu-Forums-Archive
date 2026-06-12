---
title: "[B]c and c++  compiler for ubuntu linux [/B]"
date: 2008-01-21
forum: General Help
---

### Post by mustafa_cmpe on 2008-01-21
how can i install c c++ compiler to ubuntu linux

---

### Post by anaconda on 2008-01-21
sudo apt-get install build-essential

---

### Post by mustafa_cmpe on 2008-01-21
your answer is not helpful i am beginer   you can say **Bubuntu** ok  so that more helpful answer please

---

### Post by geirha on 2008-01-21
On the panel-menu:
System -> Administration -> Synaptic package manager
Search for a package called build-essential and install it.

OR, open a terminal: Applications -> Accessories -> Terminal and type: 
```
sudo aptitude install build-essential
```

Then you'll have a c compiler called gcc, and a c++ compiler called g++.

---

### Post by mustafa_cmpe on 2008-01-21
after that it says 


Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)
in drive /cdrom/

---

### Post by geirha on 2008-01-21
> **mustafa_cmpe said:**
> after that it says 


Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)
in drive /cdrom/

In synaptic package manager, choose Settings -> Repositories, uncheck the CDROM at the bottom of the new window that pops up.

---

### Post by mustafa_cmpe on 2008-01-21
it is downloading
 now thank you

---

