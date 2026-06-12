---
title: "Can't compile gproftpd-8.2.2: Package gtk+-2.0 was not found"
date: 2005-09-02
forum: General Help
---

### Post by snowstone on 2005-09-02
Hello:

I'm trying to install [gproftpd-8.2.2](http://mange.dynup.net/linux.html) in Ubuntu 5.04.

Whenever I do ./configure, I get the error:
...
checking for gtk+-2.0 >= 1.3.13... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 1.3.13) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
---

I searched for the file gtk+-2.0.pc on my PC but it doesn't appear.
I do have installed libgtk2.0-0 and libgtk2.0-common, but I don't know how to make it work.

I would appreciate your help.

Thanks a lot.

---

### Post by Perfect Storm on 2005-09-02
When compiling you need the dev file of it.

sudo apt-get install libgtk2.0-dev

---

### Post by snowstone on 2005-09-02
I can't find the package on my repositories. Here is my sources.list:
----------------------
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted


deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) hoary universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
--------------------------

Can you tell me a repository that has the package and its dependencies?

Thanks a lot

---

### Post by snowstone on 2005-09-02
I fixed it!!!

I added the repository deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/
ans searched for libgtk2.0-dev in synaptic

found it and installed it without problems.

Thanks ;-)

---

