---
title: "apt-get 404 error"
date: 2015-10-30
forum: General Help
---

### Post by Omer_Horev on 2015-10-30
Hi,
Im using ubuntu 14.10. A few days ago i tried to install a new software using apt-get and found myself facing some errors regarding the sources.
This is the output of the apt-get update
```

..
..
..
Ign http://security.ubuntu.com utopic-security/multiverse Translation-en
Ign http://security.ubuntu.com utopic-security/restricted Translation-en_US
Ign http://security.ubuntu.com utopic-security/restricted Translation-en
Ign http://security.ubuntu.com utopic-security/universe Translation-en_US
Ign http://security.ubuntu.com utopic-security/universe Translation-en
Err http://security.ubuntu.com utopic-security/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com utopic-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Fetched 481 B in 20s (23 B/s)
Reading package lists...
..
..

```

I Tried to do a system update using the Software Updated, and it threw me the following error:

Requires installation of an untrusted packages.

This is my sources file:
```

# deb cdrom:[Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://il.old-releases.ubuntu.com/ubuntu/ utopic main restricted
deb-src http://il.old-releases.ubuntu.com/ubuntu/ utopic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://il.old-releases.ubuntu.com/ubuntu/ utopic-updates main restricted
deb-src http://il.old-releases.ubuntu.com/ubuntu/ utopic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://il.old-releases.ubuntu.com/ubuntu/ utopic universe
deb-src http://il.old-releases.ubuntu.com/ubuntu/ utopic universe
deb http://il.old-releases.ubuntu.com/ubuntu/ utopic-updates universe
deb-src http://il.old-releases.ubuntu.com/ubuntu/ utopic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://il.old-releases.ubuntu.com/ubuntu/ utopic multiverse
deb-src http://il.old-releases.ubuntu.com/ubuntu/ utopic multiverse
deb http://il.old-releases.ubuntu.com/ubuntu/ utopic-updates multiverse
deb-src http://il.old-releases.ubuntu.com/ubuntu/ utopic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://il.old-releases.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse
deb-src http://il.old-releases.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu utopic-security main restricted
deb-src http://security.ubuntu.com/ubuntu utopic-security main restricted
deb http://security.ubuntu.com/ubuntu utopic-security universe
deb-src http://security.ubuntu.com/ubuntu utopic-security universe
deb http://security.ubuntu.com/ubuntu utopic-security multiverse
deb-src http://security.ubuntu.com/ubuntu utopic-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu utopic partner
# deb-src http://archive.canonical.com/ubuntu utopic partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu utopic main
deb-src http://extras.ubuntu.com/ubuntu utopic main
deb http://archive.ubuntu.com/ubuntu utopic universe

```

Any idea facing thos errors? is my sources file outdated?

Thanks ahead,
Omer

---

### Post by deadflowr on 2015-10-30
> [COLOR=#000000]is my sources file outdated?[/COLOR]
Yes it is.

You need to upgrade to a supported release.
best bet is to backup what you want and download a fresh version from Ubuntu.com.
Just an fyi, as that is the simplest solution.

In reference to your sources.list, that is wrong.
There is only an old-releases.ubuntu.com archive repo.
There is no such thing as il.old-releases.ubuntu.com

Also, you need to #comment out everything after the last old-release line
```
deb http://security.ubuntu.com/ubuntu utopic-security main restricteddeb-src http://security.ubuntu.com/ubuntu utopic-security main restricted
deb http://security.ubuntu.com/ubuntu utopic-security universe
deb-src http://security.ubuntu.com/ubuntu utopic-security universe
deb http://security.ubuntu.com/ubuntu utopic-security multiverse
deb-src http://security.ubuntu.com/ubuntu utopic-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu utopic partner
# deb-src http://archive.canonical.com/ubuntu utopic partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu utopic main
deb-src http://extras.ubuntu.com/ubuntu utopic main
deb http://archive.ubuntu.com/ubuntu utopic universe
```

This is just an fyi on what is wrong.

I stand by the idea of backing up and downloading a new version.

---

### Post by Omer_Horev on 2015-10-30
Thanks! 

Omer

---

