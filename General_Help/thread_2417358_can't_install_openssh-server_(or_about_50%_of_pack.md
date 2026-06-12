---
title: "can't install openssh-server (or about 50% of packages I try)"
date: 2019-04-22
forum: General Help
---

### Post by asomad on 2019-04-22
Greetings. Fresh install of Lubuntu 18.04. Trying to bring in some packages to make my install usable, but every other package I attempt to install I am hit with dependency hell.
This is a fresh install, I don't get why a fresh install of an official version of Ubuntu would have so many packages unable to install due to unmet dependencies. 

I've tried general solutions to this issue with no avail. 

Here's the general issue. Many packages I try to install come back with 'unmet dependencies' and 'you have held broken packages'.. for example:
```
sudo apt-get install openssh-server 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:7.6p1-4)
                  Depends: openssh-sftp-server but it is not going to be installed
                  Recommends: ssh-import-id but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
The situation is the same with any number of packages I try to install. So one would think there's a bunch of broken stuff in here, right?
Well, I'm having trouble finding *anything* wrong. Synaptic package manage shows 0 broken packages. installing with 'sudo apt-get install -f' just yields the same. 'dpkg --configure -a' doesn't fix anything. 'sudo apt-get clean' and 'sudo apt-get autoclean' do nothing to help..

-everything is up to date according to lubuntu's software update
-I have *-main and *-updates enabled in my sources, and -security too.

I have no ideas here. I can't find any evidence of broken packages currently installed or anything with unmet dependencies currently installed. yet when I try to install any number of packages I'm met with dependency and broken package errors.

Very frustrated to say the least ](*,). I don't know what to do from here, I'm almost ready to reinstall this.

Any ideas? This is above my experience and knowledge.
 thanks

---

### Post by Tadaen_Sylvermane on 2019-04-22
Sure its an official iso? Post sources list. Definitely not a normal experience.

---

### Post by asomad on 2019-04-22
```
# deb cdrom:[Lubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner


deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

here you go thanks! And yes the ISO is an official LTS release from ubuntu's mirrors


edit: Hmmmm, it looks like universe repos are missing from the list... wtf?
I'm gonna put those in manually...

---

### Post by asomad on 2019-04-22
even after enabling Universe, nothing has changed. I'm still nowhere, sadly.
Here's my sources.list now:
```
# deb cdrom:[Lubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner


deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

---

### Post by asomad on 2019-04-22
so I removed the apt sources lists found at /var/lib/apt/lists, then updated the sources again with 'sudo apt-get update' and now everything works as it should.

I'm clueless what caused this situation, but I am glad thing are in order again.

Thanks for giving me a push to look at my sources again.

---

### Post by Tadaen_Sylvermane on 2019-04-22
I personally find the ubuntu sources list needlessly complicated with multiple entires for the same repos. Here is how I have mine, for reference anyway. Far less lines, much easier to see problems.

```
deb http://us.archive.ubuntu.com/ubuntu/ bionic main universe multiverse restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic} main universe multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main universe multiverse restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main universe multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main universe multiverse restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main universe multiverse restricted
deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner
deb http://security.ubuntu.com/ubuntu bionic-security main universe multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main universe multiverse restricted
```

---

