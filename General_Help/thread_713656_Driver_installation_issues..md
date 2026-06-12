---
title: "Driver installation issues."
date: 2008-03-03
forum: General Help
---

### Post by SamAdam on 2008-03-03
So I have the tuner card HVR-1600.  Now I found a beta driver that I am having issues installing.  the filename is called cx18-03d4d8d84c4f.tar.bz2.  *side note, i can type that from memory ive typed it so many times...*  So i did the unzip stuff, and now have a folder with the same name...yada yada yada.  Now in the instructions I have to run "make"  then "make install" and "make unload"  my issue is this, I can not run make.  I switch the the new folder directory and all that.  

This is what i get:
[sam@sam-desktop:/tmp/cx18-03d4d8d84c4f$ make
make -C /tmp/cx18-03d4d8d84c4f/v4l
make[1]: Entering directory '/tmp/cx18-03d4d8d84c4f/v4l'
Updating/creating .config
Preparing to compile for kernel version 2.6.22
File not found: /lib/modules/2.6.22-14-generic/build/.config at ./scripts/make_k
config.pl line 32, <IN> line 4
make [1]: *** No rule to make target '.myconfig', needed by 'config-compat.h'. S
top.
make[1]: Leaving driectory '/tmp/cx18-03d4d8d84c4f/v4l'
make: [all] Error 2

Any suggestions???

---

### Post by logos34 on 2008-03-03
are you sure it's not ./configure, make, make install?

Double check the README and INSTALL files.  

Also, you should have the pkg **build-essential** installed.

---

### Post by SamAdam on 2008-03-03
> **logos34 said:**
> are you sure it's not ./configure, make, make install?

Double check the README and INSTALL files.  

Also, you should have the pkg **build-essential** installed.

for some reason it wont let me view the readme file.  and I have tried ./configure.  nothing happens.

---

### Post by odiseo77 on 2008-03-03
Do you have the kernel headers installed? First check if they're installed or not:

```
dpkg -l linux-headers-`uname -r`
```

If they're not installed, proceed to install them:

```
sudo apt-get install linux-headers-`uname -r`
```

(then try to recompile the driver)

---

