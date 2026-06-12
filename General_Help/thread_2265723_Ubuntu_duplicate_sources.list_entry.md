---
title: "Ubuntu duplicate sources.list entry"
date: 2015-02-17
forum: General Help
---

### Post by polochamps on 2015-02-17
Hi,

When I update via terminal I get this:

```
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-amd64_Packages)

W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)


W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-amd64_Packages)


W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)


W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages)


W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)


W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages)


W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)

```

My source.list

```
# deb cdrom:[elementary OS 0.3 _Freya_ - Daily amd64 (20150208)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ph.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ph.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty universe
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ph.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-backports universe restricted multiverse main
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://security.ubuntu.com/ubuntu/ trusty-security universe restricted multiverse main
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-proposed universe restricted multiverse main
```

Thank you

---

### Post by ian-weisser on 2015-02-17
Use your favorite text editor to delete the duplicate entries.

Example:
```
## One set
deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse

## Other set
deb http://security.ubuntu.com/ubuntu/ trusty-security universe restricted multiverse main
```

---

### Post by polochamps on 2015-02-17
> **ian-weisser said:**
> Use your favorite text editor to delete the duplicate entries.

Example:
```
## One set
deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse

## Other set
deb http://security.ubuntu.com/ubuntu/ trusty-security universe restricted multiverse main
```


Many thanks man!

---

