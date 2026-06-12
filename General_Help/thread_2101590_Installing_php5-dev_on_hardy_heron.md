---
title: "Installing php5-dev on hardy heron"
date: 2013-01-05
forum: General Help
---

### Post by phpserver on 2013-01-05
I am trying to install php5-dev with

```
sudo apt-get install php5-dev
```

but i get this error

[PHP]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-dev: Depends: autoconf but it is not installable
            Depends: automake1.4 but it is not installable
            Depends: libssl-dev but it is not going to be installed
            Depends: libtool but it is not installable
            Depends: shtool but it is not installable
E: Broken packages[/PHP]

i have tried updating and even looking at my sources.list but the error won't go away.What should i do?.

---

### Post by dino99 on 2013-01-05
you get some version conflicts. Are you using also some non genuine repos like ppa(s) ?
First check the active repos, then clean the system as much possible (clean/autoclean/autoremove), then check that the conflicting packages are the genuine ones (in case downgrade them)

If you cant get installation, then you can "force" it using dpkg

(sudo dpkg -i --force-all ....  see the manpage)

[https://launchpad.net/ubuntu/+source/php5](https://launchpad.net/ubuntu/+source/php5)

---

### Post by phpserver on 2013-01-05
I have some ppa's and also did some uncommenting

Here is how my sources.list looks like

```
# 
# deb cdrom:[Ubuntu 8.04.4 _hardy Heron_ - Release i386 (20100121.2)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04.4 _hardy Heron_ - Release i386 (20100121.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://ppa.launchpad.net/gearman-developers/ppa/ubuntu hardy main 
deb-src http://ppa.launchpad.net/gearman-developers/ppa/ubuntu hardy main

deb http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu hardy main 
deb-src http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu hardy main  
```

Should i comment on ppas and some other sources?.

---

