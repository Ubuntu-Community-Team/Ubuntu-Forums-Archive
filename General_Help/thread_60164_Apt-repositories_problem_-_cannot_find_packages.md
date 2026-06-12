---
title: "Apt-repositories problem - cannot find packages"
date: 2005-08-26
forum: General Help
---

### Post by Muffe on 2005-08-26
I have a problem with the apt-get command. If I try to install for example either msttcorefonts, sun-j2re1.5, acroread or nvu, i only get a message similar to this: 

```
root@acer:/etc/apt # apt-get install nvu
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nvu
root@acer:/etc/apt #
```

or this:

```
root@acer:/etc/apt # apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
root@acer:/etc/apt #
```

or this:

```
root@acer:/etc/apt # apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mozilla-acroread acroread-plugins
E: Package acroread has no installation candidate
root@acer:/etc/apt #
```


My sources.list looks like this:

```
# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://no.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://no.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu hoary universe
deb-src http://no.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe


# Diverse
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

# deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
# deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted

```

I have of curse done several apt-get update commands.

Thanks.

---

### Post by crmanski on 2005-08-26
I had the same problem with the us. repositories and I read somewhere to remove the us. from [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) and it cleared up a similar problem.

Maybe changing yours to just [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) on all the lines that have no.archive.ubuntu.com?

---

### Post by Muffe on 2005-08-27
It didn't solve my problem. Still the same error messages.

---

### Post by blackant on 2005-08-27
Same problem with me too.
I read around the forum, and it seems like the backport repositories got some error.

---

### Post by Muffe on 2005-08-27
Seems like others have a similar problem: [http://ubuntuforums.org/showthread.php?t=59229](http://ubuntuforums.org/showthread.php?t=59229)

---

