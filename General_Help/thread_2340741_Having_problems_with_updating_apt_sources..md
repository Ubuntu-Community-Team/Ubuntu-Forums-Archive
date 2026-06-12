---
title: "Having problems with updating apt sources."
date: 2016-10-21
forum: General Help
---

### Post by kevdog on 2016-10-21
My /etc/apt/sources.list is listed below. 

When I try updating, its seems it hangs on:
10% [Connecting to us.archive.ubuntu.com (2001:67c:1562::16)] [Connecting to security.ubuntu.com (200

Is there a problems with the servers?

```

$ more /etc/apt/sources.list
# deb cdrom:[Ubuntu MATE 14.04.2 _Trusty Tahr_ - LTS i386 (20150323)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

```

---

### Post by TheFu on 2016-10-21
Some of the internet DNS servers are being attacked today.  Plus, might be worth trying IPv4 addresses instead of IPv6 stuff.  If you can wait and there haven't been any issues previously, try again later.
You can use a web browser to check those problem locations ... after all, http is just http, right?  Does it work?

---

### Post by kevdog on 2016-10-21
Sorry for my lack of insight, however where am I trying IPv6 stuff? Thanks for explanation.

---

### Post by TheFu on 2016-10-21
> Connecting to us.archive.ubuntu.com (2001:67c:1562::16)] ... that's IPv6.

---

### Post by kevdog on 2016-10-21
So how do I prevent that?

No worries

I figured it out: [http://tecadmin.net/disable-ipv6-on-linux/#](http://tecadmin.net/disable-ipv6-on-linux/#)

Thanks for your help -- much faster now!!!!

I also found this site extremely helpful for auto regeneration of the /etc/apt/sources.list.  Pretty cool website: [https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

---

