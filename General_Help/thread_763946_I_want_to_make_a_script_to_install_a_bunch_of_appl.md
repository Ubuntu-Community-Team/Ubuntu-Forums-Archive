---
title: "I want to make a script to install a bunch of applications"
date: 2008-04-23
forum: General Help
---

### Post by JAGGEDSPHERE on 2008-04-23
Hi, I would like to know how I might go about creating an executable that would allow me to install a bunch of applications.
When 8.10 comes out I would like to be able to just run a script that installs all of the software that I use but doesn't come pre-installed on 8.10.
These could be anything from .deb files, and things in the repos. 

Any ideas/leads would be just great.
Thanks
Richard
Ottawa, On

---

### Post by Archimedes0212 on 2008-07-24
if the installations can all be done from the command line, you can write a script in a language such as Perl.  I don't remember the command offhand, but it is easily google-able - it allows you to execute terminal commands 
(might be System("stringgoeshere");)

Anyways, you can then run the perl script and it should go through all the commands you specify and installation should go by fine.

hope this helps

---

### Post by Potatoj316 on 2008-07-24
If your installing from repos you could use this command
```
sudo aptitude install package1, package2, package3
```
if you want to install .deb packages you already have I think you use dpkg.  You can put these 2 lines together in a file and calle it whatever.sh

---

### Post by dje on 2008-07-24
> **Potatoj316 said:**
> If your installing from repos you could use this command
```
sudo aptitude install package1, package2, package3
```
if you want to install .deb packages you already have I think you use dpkg.  You can put these 2 lines together in a file and calle it whatever.sh

you don't use commas to separate packages otherwise it thinks the package name has a comma in and it can't find the package then. Also IMHO i prefer apt:
```
sudo apt-get install package1 package2 package3
```

hope that helps,
dje

---

### Post by Potatoj316 on 2008-07-24
> **dje said:**
> you don't use commas to separate packages otherwise it thinks the package name has a comma in and it can't find the package then. Also IMHO i prefer apt:
```
sudo apt-get install package1 package2 package3
```

hope that helps,
dje

Yeah, forgot about the no commas, I dont usually install more than 1 package at a time, and I prefer aptitude, it has more features than apt-get

---

### Post by bodhi.zazen on 2008-07-24
You do not need sudo.

```
apt-get -y package1 package2 package3
```

then 

sudo script

---

### Post by dje on 2008-07-24
> **bodhi.zazen said:**
> You do not need sudo.

```
apt-get -y package1 package2 package3
```

then 

sudo script

ah yes forgot about that and also the -y flag :)

---

