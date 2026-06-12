---
title: "Upgrade Life-cycle?"
date: 2004-10-26
forum: General Help
---

### Post by SVen2000 on 2004-10-26
How should my sources.list and apt.conf look like, if:

- I only want to get security updates by default
- I want to upgrade the whole system whenever a new ubuntu release comes out
- from time to time, I want to install "brand-new" software, e.g. once firefox 1.0 is releaesed.

Ah, and I don't know what the sources.list and apt-conf look like by default since I was upgrading from debian/sarge.

---

### Post by triad169 on 2004-10-26
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041013)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted


That is default sources.list of Ubuntu Install.

---

