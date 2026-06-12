---
title: "how to install acrobat reader 7"
date: 2005-04-09
forum: General Help
---

### Post by jhands on 2005-04-09
i downloaded acrobat reader 7 and its called   AdobeReader_enu-7.0.0-1.i386.rpm 

 dont know how to install it. any suggestions?

---

### Post by humanity_to_others on 2005-04-09
adobe 7 is in the repositories
```
deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main
```
may be you should look at this page: [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by humanity_to_others on 2005-04-09
adobe 7 is in the repositories
```
deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main
```
Maybe you sholud look at this page: [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by jhands on 2005-04-09
i added those rpositories but synaptic doesnt show it? when i apt-get it installed the old one. what should i do while after typing apt-get install...

---

### Post by artinla on 2005-04-09
Did you install the public gpg key for marillat?

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -

I think the Ubuntu Multimedia howto explains most of how to get marillat to work.

Art

---

### Post by sinbad782 on 2005-04-10
You can also add the [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) repositories - these have an installer for the realplayer RPM file as well as acroread. There's some other audio and video programs in there as well. 

Add the following to your /etc/apt/sources.list file:

deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free

L8rs,

PJS

---

