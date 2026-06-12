---
title: "Installing RAR?"
date: 2007-01-15
forum: General Help
---

### Post by iangoeth on 2007-01-15
I read a tutorial on an ubuntu blog/forum whatever somewhere around here that said I could install RAR/UNRAR through apt if I added universe and multiverse repos. Well here's what my sources.list looks like

```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Right, right? Wrong. I go and try to install rar through apt and get this
```

ian@saint:~$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
ian@saint:~$

```

So I think no sweat right, it's available for download from rarsoft's page. I go grab it, extract, ./configure, make then sudo make install, it's all good. But then bad things happen from there.
```

ian@saint:/media/zealot/backups/drivers$ unrar webcam\ drivers.rar
unrar: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by unrar)
ian@saint:/media/zealot/backups/drivers$

```
Of course if I try to apt-cache search glibc, I find no such version. There is glibc-dev 2.2, but no 2.4.

Any ideas?

---

### Post by mykalreborn on 2007-01-15
you can try [easy ubuntu]("http://easyubuntu.freecontrib.org/"). it also can install .ace support and countless other things ;)

---

### Post by bailout on 2007-01-15
From a quick look at your sources it doesn't look like you have multiverse enabled. You have backports multiverse but not ubuntu multiverse. Just add multiverse to the third 'block' down.

---

### Post by iangoeth on 2007-01-15
> **bailout said:**
> From a quick look at your sources it doesn't look like you have multiverse enabled. You have backports multiverse but not ubuntu multiverse. Just add multiverse to the third 'block' down.

Oh, thank you for that. That made rar and unrar show up in apt-cache. I installed them that way, but it still tells me that I need glibc 2.4, which is still missing from apt-cache.

I just thought I would edit this post to say that I tried easyubuntu to install rar support as well as a few other things, and it told me that the package installs were broken after it downloaded them.

---

### Post by Azncop on 2007-01-15
[http://ftp.gnu.org/gnu/glibc/glibc-2.4.tar.bz2](http://ftp.gnu.org/gnu/glibc/glibc-2.4.tar.bz2)

---

