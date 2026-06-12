---
title: "installing acronis on server 7.o4"
date: 2007-08-28
forum: General Help
---

### Post by Crasher on 2007-08-28
Hi Has anyone been able to get acronis true image server to install succesfully to server 7.04?
I get part way thru the module compile for snapapi and it errors and fails ??any thoughts?
I have posted this to acronis support so if I get a fix from them I will post it here

---

### Post by akane on 2007-08-29
I'm having the same exact issue - let me know what Acronis support says. :)

---

### Post by Crasher on 2007-08-29
Hi this is acronis answer...I haven't tried it yet so if you get to it before me please post your result......

Please do the following:

- Download snapapi package:
[http://download.acronis.com/sl/bxnbkspyupfdzqhiympr/support/snapapi26_modules-0.7.24-1.noarch.rpm](http://download.acronis.com/sl/bxnbkspyupfdzqhiympr/support/snapapi26_modules-0.7.24-1.noarch.rpm)
- Install the downloaded package:
#rpm -Uvh snapapi26_modules-0.7.24-1.noarch.rpm
- Load the module tarball to DKMS:
#dkms ldtarball --archive=/usr/lib/Acronis/kernel_modules/snapapi26_modules-0.7.24-1.noarch.tar.gz
- Build and install the new module:
#dkms build -m snapapi26 -v 0.7.24 \
-k <KERNEL_VERSRION> --config <CONFIG_FILE> --arch <KERNEL_ARCH> \ --kernelsourcedir <PATH_TO_KERNEL_SOURCES> #dkms install -m snapapi26 -v 0.7.24 \ -k <KERNEL_VERSRION> --config <CONFIG_FILE> --arch <KERNEL_ARCH> \ --kernelsourcedir <PATH_TO_KERNEL_SOURCES>

---

### Post by Crasher on 2007-08-29
Hi I attempted the fix but got stumpted at the first hurdle.....

Downloaded the file, however when installing get the following error output-

rlpb@rlpb:~$ sudo rpm -Uvh /home/rlpb/snapapi26_modules-0.7.24-1.noarch.rpm 

error: Failed dependencies: /bin/sh is needed by snapapi26_modules-0.7.24-1.noarch
        bash is needed by snapapi26_modules-0.7.24-1.noarch


However sh is in the /bin directory and bash is installed???

I have again requested acronis support.

---

### Post by akane on 2007-08-30
I was able to get the RPM file installed by converting it to a .deb using alien.
```
sudo apt-get install alien
```
```
sudo alien snapapi26_modules-0.7.24-1.noarch.rpm
```
```
sudo dpkg -i snapapi26-modules-0.7.24-1.noarch.deb
```

But I have no clue what they are talking about when referring to DKMS .. let me know what they say. :)

---

### Post by Crasher on 2007-09-03
Got it going.......if you cannot follow this grab the howto file from acronis....[http://www.acronis.com/r/support/en/kb/492/HOWTO.INSTALL](http://www.acronis.com/r/support/en/kb/492/HOWTO.INSTALL)
this will tell you how to get the info for each part of the command.

Please do the following:

- Download snapapi package:
[http://download.acronis.com/sl/bxnbkspyupfdzqhiympr/support/snapapi26_modules-0.7.24-1.noarch.rpm](http://download.acronis.com/sl/bxnbkspyupfdzqhiympr/support/snapapi26_modules-0.7.24-1.noarch.rpm)
- Install the downloaded package:
#rpm -Uvh snapapi26_modules-0.7.24-1.noarch.rpm
- Load the module tarball to DKMS:
#dkms ldtarball --archive=/usr/lib/Acronis/kernel_modules/snapapi26_modules-0.7.24-1.noarch.tar.gz
- Build and install the new module:
#dkms build -m snapapi26 -v 0.7.24 \
-k <KERNEL_VERSRION> --config <CONFIG_FILE> --arch <KERNEL_ARCH> \ --kernelsourcedir <PATH_TO_KERNEL_SOURCES> #dkms install -m snapapi26 -v 0.7.24 \ -k <KERNEL_VERSRION> --config <CONFIG_FILE> --arch <KERNEL_ARCH> \ --kernelsourcedir <PATH_TO_KERNEL_SOURCES>

My commands were as follows....

rlpb@rlpb:~$ sudo dkms build -m snapapi26 -v 0.7.24 \ -k 2.6.20-16-server --config config-2.6.20-16-server --arch i686 \ --kernelsourcedir /usr/src/

rlpb@rlpb:~$ sudo dkms install -m snapapi26 -v 0.7.24 \ -k 2.6.20-16-server --config config-2.6.20-16-server --arch i686 \ --kernelsourcedir /usr/src/

Good luck...let me know how you get on

---

### Post by zolero on 2008-06-07
I have similar issues with ATIES 9.1 Linux on 8.04 LTS Hardy. In addition I can't even grab the RPM package by following the links. Error: "File not found." Do I missed something...  :?: :-k

---

