---
title: "Missing Xlibs and header files?"
date: 2005-10-27
forum: General Help
---

### Post by p0ltergeist on 2005-10-27
I'm attempting to install QT ([www.trolltech.com](www.trolltech.com)) but upon running "make" I'm getting the following errors:

```


In file included from ../../include/QtGui/private/qt_x11_p.h:1, from kernel/qapplication.cpp:51:
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:50:22: error: X11/Xlib.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:55:23: error: X11/Xutil.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:56:21: error: X11/Xos.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:57:23: error: X11/Xatom.h: No such file or directory


```

Upon seeing this, I went to /usr/include/X11 where I should find header files for programming with Xlib and the like, but I'm only seeing a couple directories in there which don't contain anything relevant. 

I have searched through synaptic, installed the latest version of xlib and installed many other libraries that I could find. I have even installed every package that has a name starting with the letter 'x' but that still has availed me nothing.

---

### Post by Remmelas on 2005-10-27
you have the lib's installed you say, but, are they the runtime shared libraries, or the development libraries.
for example Xlib.h is in libx11-dev, so sudo apt-get install libx11-dev
or, to make it easier on yourself, install the x11-dev meta package with sudo apt-get install x11-dev
if you aren't going to develop with QT you could also just install the runtime's with sudo apt-get install libqt3-mt

---

### Post by phodifoo on 2006-02-04
Can someone help me ? 
I am missing something:

root@ubuntu:~# apt-get install libx11-dev
Reading package lists... Done
Building dependency tree... Done
Package libx11-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libx11-dev has no installation candidate

or 

root@ubuntu:~# apt-get install x11-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package x11-dev

---

### Post by lamego on 2006-02-04
The correct package names come from:
```
sudo apt-cache search xlibs dev
```

---

### Post by phodifoo on 2006-02-04
doesn't seem to work either: (it returns nothing)

root@ubuntu:~# apt-cache search xlibs dev
root@ubuntu:~#

---

### Post by lamego on 2006-02-04
lamego@ubuntu-desktop:~$ sudo apt-cache search xlibs dev
xlibs-dev - X Window System client library development files transitional package
xlibs-static-dev - X Window System client library development files
xlibs-static-pic - X Window System client extension library PIC archives
lamego@ubuntu-desktop:~$

Problem:
You don't have the required repositores enabled:
```
sudo gedit /etc/apt/source.list
```
Uncomment the universe and multiverse repositories, then update with:
```
sudo apt-get update
```

---

### Post by phodifoo on 2006-02-04
root@ubuntu:~# apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Fetched 1B in 0s (1B/s)
Reading package lists... Done
root@ubuntu:~# apt-cache search xlibs dev
root@ubuntu:~#


here is my /etc/apt/sources.list
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by phodifoo on 2006-02-04
this did the job:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse



THANKS !!!!

---

### Post by oneiropolos on 2006-03-23
guys, i am missing these Xlibs too but :
vagkos@ubuntu:~$** sudo apt-cache search xlibs dev**
vagkos@ubuntu:~$
or 
vagkos@ubuntu:~$ **sudo apt-get install libx11-dev**
Reading package lists... Done
Building dependency tree... Done
Package libx11-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libx11-dev has no installation candidate
or
 **sudo apt-get install x11-dev**
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package x11-dev

here are my repositories:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe


is something missing here?

---

