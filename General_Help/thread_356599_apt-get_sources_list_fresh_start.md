---
title: "apt-get sources list fresh start"
date: 2007-02-08
forum: General Help
---

### Post by mpgarate on 2007-02-08
Ive been getting some errors with apt-get, and I believe I messed up my sources.list file. Is there a place I could download the original to replace it with and start over?

I just installed ubuntu on this machine yesterday, although I am pretty familiar with it already from previous machines.

---

### Post by ~LoKe on 2007-02-08
You could always paste your list here so we could fix it for you.
```
cat /etc/apt/sources.list
```

Or just look for a backup on the apt folder, perhaps the original is hanging around somewhere:
```
ls /etc/apt/|grep source
```

---

### Post by taurus on 2007-02-08
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by dannyboy79 on 2007-02-08
> **mpgarate said:**
> Ive been getting some errors with apt-get, and I believe I messed up my sources.list file. Is there a place I could download the original to replace it with and start over?

I just installed ubuntu on this machine yesterday, although I am pretty familiar with it already from previous machines.

if it states anything about linux-kernel-generic or anything like that, it's a global issue. they're not in the repos yet so just relax, you didn't do anything wrong. otherwise, you can copy it from the live cd.

---

### Post by mpgarate on 2007-02-08
thanks for the quick response. Here is the result of the first command:

> deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
rpm [http://gstreamer.freedesktop.org/pkg/](http://gstreamer.freedesktop.org/pkg/) fedora/4/i386 deps gst
rpm-src [http://gstreamer.freedesktop.org/pkg/](http://gstreamer.freedesktop.org/pkg/) fedora/4/i386 deps gst



apt-get specifically said line 31 could not be read

---

### Post by ~LoKe on 2007-02-08
```
gksu gedit /etc/apt/sources.list
```
Then remove these lines:
> rpm [http://gstreamer.freedesktop.org/pkg/](http://gstreamer.freedesktop.org/pkg/) fedora/4/i386 deps gst
rpm-src [http://gstreamer.freedesktop.org/pkg/](http://gstreamer.freedesktop.org/pkg/) fedora/4/i386 deps gst
RPM is Fedora based, Ubuntu is Debian based.

---

### Post by taurus on 2007-02-08
You need to edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out the last two lines by placing a # in front of them.

```

#rpm http://gstreamer.freedesktop.org/pkg/ fedora/4/i386 deps gst
#rpm-src http://gstreamer.freedesktop.org/pkg/ fedora/4/i386 deps gst

```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ~LoKe on 2007-02-08
Might I suggest a different sources.list?

Use at your own risk:
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by cleentrax on 2007-02-08
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

This list generator is an interesting tool, but of course I would back up your original before trying it out.

---

### Post by mpgarate on 2007-02-08
thank you all very much for the fast responses and multiple solutions! I used the source-o-matic, and now its working perfectly. Ill be more careful about debian vs fedora.

---

