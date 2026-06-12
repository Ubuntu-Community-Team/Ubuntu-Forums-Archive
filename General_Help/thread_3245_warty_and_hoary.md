---
title: "warty and hoary"
date: 2004-11-04
forum: General Help
---

### Post by BlackFenix on 2004-11-04
How i can use some package from warty and other from hoary ?

---

### Post by Magneto on 2004-11-04
sudo nano -w /etc/apt/sources.list

and add these lines

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main 

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main





add universe multiverse or restricted after main for more packages


google - apt-get  sources.list

---

### Post by BlackFenix on 2004-11-04
ok.
How i can define the default version and how i can install packages from warty or hoary ? It's like debian ?

Debian example:


/etc/apt/apt.conf -> APT::Default-Release "Warty"

aptitude -t Hoary install <package>

---

