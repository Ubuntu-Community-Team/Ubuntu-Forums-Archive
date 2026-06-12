---
title: "Cannot install libgtk2.0devel"
date: 2006-07-15
forum: General Help
---

### Post by lduperval on 2006-07-15
Hi,

I am trying to compile an application that requires the libgtk2 development environment.

Whenever I try to install, I get this error:

```

libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.8.17-1ubuntu5) but 2.8.18-0ubuntu2 is to be installed
 Depends: libglib2.0-dev but it is not going to be installed
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libatk1.0-dev but it is not going to be installed

```

So, how do I get this installed?

Thanks,

L

---

### Post by givré on 2006-07-15
you have to upgrade first
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by lduperval on 2006-07-15
I did and I get 0 packages updated. I seem to be at the latest versions. :( 

L

---

### Post by givré on 2006-07-15
not yet :cool: 
What is your /etc/apt/source.list, you should uncomment line about dapper-update.

---

### Post by lduperval on 2006-07-15
Hmmm.. it looks ok. Although I see that the libgtk version on my machine is 2.8.18 while the latest -dev available is 2.8.17. So something is a little screwy.

L

```

deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by givré on 2006-07-15
Change that
```
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
```
to that
```
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
```

---

### Post by lduperval on 2006-07-16
Excellent, it works, thanks!

L

---

