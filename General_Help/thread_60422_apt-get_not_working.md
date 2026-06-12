---
title: "apt-get not working?"
date: 2005-08-27
forum: General Help
---

### Post by bean on 2005-08-27
Hi there,

Im trying to get some codecs downloaded, going by ubuntuguide's instructions, but i keep on getting a few errors, and im not able to get anything really through apt-get.

root@hbox:~ # apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs
root@hbox:~ # apt-get w32codecs

i cant find any of the packages on [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Here is my sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe



Im not really sure at all why nothings working?.

---

### Post by NateC on 2005-08-27
Add the backport servers.

---

### Post by jasmuz on 2005-08-27
add these repositories to the list:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

Save and close, then sudo apt-get update

finally sudo apt-get install w32codecs

---

### Post by DJ_Max on 2005-08-27
[http://amd64.ubuntuguide.org/#extrarepositories](http://amd64.ubuntuguide.org/#extrarepositories)

---

### Post by bean on 2005-08-27
I put in the list from ubuntu guide, updates, and then got this:

root@hbox:~ # apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

***
not to worry, i think other things are working now.

and thanks for the quick responces guys  \\:D/

---

