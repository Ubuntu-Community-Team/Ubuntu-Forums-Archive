---
title: "need help with installing virtualbox"
date: 2007-05-02
forum: General Help
---

### Post by stalefist on 2007-05-02
im using this guide to help me install it: [http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu)
i downloaded the udgy binary since im using that, and when i get to the apt-get it says :

nick@frosty-linux:~$ sudo apt-get install bcc iasl xsltproc xalan libxalan110-dev uuid-dev zlib1g-dev libidl-dev libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev libasound2-dev libstdc++5 linux-headers-`uname -r` build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcc

i tried taking out the bcc package but it still wasnt finding anything, am i missing a repo or something?

---

### Post by taurus on 2007-05-02
Well, you can tell us which release you are running and the content of your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by stalefist on 2007-05-03
im running edgy eft. this is the log:
# 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) edgy main main-all

---

### Post by taurus on 2007-05-03
Did you upgrade from Dapper to Edgy or something?

---

### Post by stalefist on 2007-05-03
nevermind, i got it to work using the binaries. thats odd, it worked today but wasnt working before. hrm....

---

### Post by coorangreeny on 2007-09-04
Please bear with me, I'm not only new to Ubuntu, I'm new to Linux...

I also want to install Virtualbox on an Ubuntu 6.06 machine.

When I try to unpackage virtualbox_1.5.0-24069-1_Ubuntu_dapper_i386.deb, I get an error message:  Dependency is not satisfiable: libxalan110

Can someone patient please explain what all this means?

Steep learning curve.

Mike.:)

---

### Post by maybeway36 on 2007-09-04
Use the apt repository instead. That way it can do the dependencies for you. (Synaptic and Adept let you add deb lines and auth keys)

---

