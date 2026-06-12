---
title: "How do I install 28310-neutral-1.13a.tar.gz?"
date: 2007-08-19
forum: General Help
---

### Post by sdim on 2007-08-19
Hi,there.
Just downloaded _28310-neutral-1.13a.tar.gz_,which is a .tar package for installing mouse cursors.I read a tutorial about installing .tar.gz files,but the command MAKE does not do anything.
Any ideas about how to install the package?
(Please be as clear  as possible,as I am a novice Ubuntu user).

Thank you.

---

### Post by taurus on 2007-08-19
You may have to do something like

```
tar xvzf 28310-neutral-1.13a.tar.gz
cd 28310-neutral-1.13a
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure
make
sudo make install
[COLOR="Blue"]-or-[/COLOR]
sudo checkinstall
```
Otherwise, read the README of INSTALL for instructions.

```
more INSTALL
```

---

### Post by sdim on 2007-08-19
Thank you for answering,bit it doesn't work.It tells me "No such file or directory" and "error not repairable"(in Greek),"tar: Child returned status 2"  and it doesn't go on with the installation.

---

### Post by g2g591 on 2007-08-19
do you know for sure if its a source package?

---

### Post by taurus on 2007-08-19
Where did you download it from, 28310-neutral-1.13a.tar.gz?  Sounds to me like it's corrupted while downloading to your machine.

---

