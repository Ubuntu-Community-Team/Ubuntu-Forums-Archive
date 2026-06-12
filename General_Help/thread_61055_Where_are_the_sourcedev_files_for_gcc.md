---
title: "Where are the source/dev files for gcc?"
date: 2005-08-30
forum: General Help
---

### Post by mond on 2005-08-30
Hi

I have the following source.list file (shown below) but I can't find the source/dev package for gcc (using Synaptic). Is there a Ubuntu package for them? Or will I have to get them from the GCC homepage? (If so, I take it there would be a Makefile rule to just install the source files?)

Thanks in advance!

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://gb.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://gb.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://gb.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by DJ_Max on 2005-08-30
What are you trying to do? If you want gcc & g++ to compile apps.
```
sudo apt-get install build-essential
```

If you just want the source.
```
apt-get source gcc g++
```

---

### Post by mond on 2005-08-30
I already have gcc 3.3.5 installed. I want to compile [GHDL](http://ghdl.free.fr), which implements a VHDL front end for gcc. To be able to install GHDL from source I need the gcc development files because the  installation procedure is to move the GHDL files into gcc's folder and then do a configure and make.

As ```
apt-get source gcc
``` will get the source files (I just need the core part, I think) can I then just move them into /usr/lib/gcc-lib/i486-linux/3.3.5/?

Thanks again.

---

