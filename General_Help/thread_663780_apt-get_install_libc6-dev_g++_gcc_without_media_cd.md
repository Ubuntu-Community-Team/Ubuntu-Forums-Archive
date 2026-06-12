---
title: "apt-get install libc6-dev g++ gcc without media cd?"
date: 2008-01-10
forum: General Help
---

### Post by MrChonks on 2008-01-10
Hello all,

I am currently trying to install libc6-dev, g++ and gcc remotely via SSH.  The issue I am experiencing is that it asks me for the media cd.  Not wanting to bother my wife to dig through my unlabeled linux CDs, how would I go about getting this from the repositories instead of the CD?

Thanks,
Chonks

---

### Post by narehart on 2008-01-10
Open up software sources and uncheck the box that calls on the CD for packages.

---

### Post by MrChonks on 2008-01-10
Keep in mind, this is something I would like to do via SSH.  That is my current need.  No gui at this moment.

---

### Post by MartynA on 2008-01-10
This is probably in /etc/apt/sources.list. If you have any deb cdrom lines like so:

deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

comment them with a #

I think thats right anyway.

---

### Post by zvacet on 2008-01-10
```
gsudo gedit /etc/apt/sources.list
```

Put # sign in front of  line deb cdrom

Save and close.
```
sudo apt-get update
```

---

### Post by ~LoKe on 2008-01-10
> **MartynA said:**
> I think thats right anyway.

Yep.  You can open it up with any text editor, so if it's CLI:
```
sudo nano /etc/apt/sources.list
```
Then comment out the line,  It should be the first line.

---

### Post by MrChonks on 2008-01-10
heh...I that was all the way at the top of the list and I never even saw it.  Thanks for your help, guys.

---

