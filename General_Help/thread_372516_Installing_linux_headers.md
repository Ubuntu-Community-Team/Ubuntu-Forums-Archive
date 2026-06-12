---
title: "Installing linux headers"
date: 2007-02-28
forum: General Help
---

### Post by trek on 2007-02-28
I am recompiling an old version of the kernel (2.6.16).  I have the full sources.  Do I also need the headers?  If so, where could I find them at?

---

### Post by Malakia on 2007-02-28
First question did you install build-essential and all the stuff that you need to build the kernel? If you didn't do that you need to.

```
 sudo aptitude install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
```

If you did once the kernel is compiled you will have to .deb files to install the header file and the kernel image.

---

### Post by zvacet on 2007-02-28
```
uname -a
```
and just for example what I will have to do 
```
sudo apt-get install linux-headers-2.6.17-11-generic 
```
You will replace it with your own.

---

