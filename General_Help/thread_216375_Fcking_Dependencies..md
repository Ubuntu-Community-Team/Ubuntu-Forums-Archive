---
title: "F*cking Dependencies."
date: 2006-07-15
forum: General Help
---

### Post by Unknowndeepness on 2006-07-15
Hi there.

Ive got a problem, nomatter what i try to install it sais this:

```

The following packages have unmet dependencies:
  kopete: Depends: libspeex1 (>= 1.1.12-1) but 1.1.11.1-1 is to be installed
          Depends: ortp-0.7.1 but it is not installable or
                   libortp but it is not installable or
                   ortp (= 0.7.1) but it is not installable
  rhtvision2.0.2: Depends: libstdc++2.10-glibc2.2 (>= 1:2.95.4-0.010810) but it is not going to be installed
                  Depends: xlibs (> 4.1.0) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

and if i do a "apt-get -f install":

```
The following extra packages will be installed:
  libstdc++2.10-glibc2.2
The following packages will be REMOVED:
  kopete kubuntu-desktop rhtvision2.0.2
The following NEW packages will be installed:
  libstdc++2.10-glibc2.2
0 upgraded, 1 newly installed, 3 to remove and 31 not upgraded.
4 not fully installed or removed.
Need to get 329kB of archives.
After unpacking 21.7MB disk space will be freed.
Do you want to continue [Y/n]?
```

Remove kubuntu-desktop? Err.
Wont that like.. delete kde and everything?

What to do? :P

---

### Post by Ramses de Norre on 2006-07-15
What's your /etc/apt/sources.list like? Could you post the contents here?

---

### Post by Unknowndeepness on 2006-07-15
Sure, here you go:

```

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
## deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.

deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

deb http://kubuntu.org/packages/amarok-141 dapper main

deb http://apt.cerkinfo.be/ unstable main contrib
deb-src http://apt.cerkinfo.be/ unstable main contrib

```

---

### Post by Ramses de Norre on 2006-07-15
Have you installed some non-official-repo version of kopete? Because the dependencies apt is complaining about aren't listed in the official package properties ([link]("http://packages.ubuntulinux.org/dapper/kde/kopete")).

---

### Post by Unknowndeepness on 2006-07-15
Yep! :)

```

deep@home:~$ kopete --version
Qt: 3.3.6
KDE: 3.5.2
Kopete: 0.12.0
```

Edit: But 0.12 wont start from time to time. Dunno why, but i end up using 1.11.<something> :S

---

### Post by Unknowndeepness on 2006-07-15
Noone had anything to solve this?

---

### Post by cptnapalm on 2006-07-15
kubuntu-desktop is just a meta package.  It does not actually contain anything (it just makes installation of KDE easy), so removing it should not do anything to your KDE installation.

---

### Post by Anduu on 2006-07-15
Let it remove kubuntu desktop then when all is said and done you can reinstall it.

---

### Post by az on 2006-07-15
> **Unknowndeepness said:**
> Sure, here you go:

```

deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted


```

I think you want that to be 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

and not deb-src.....

---

