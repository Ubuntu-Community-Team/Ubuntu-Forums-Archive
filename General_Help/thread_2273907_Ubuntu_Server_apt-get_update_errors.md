---
title: "Ubuntu Server apt-get update errors"
date: 2015-04-16
forum: General Help
---

### Post by joelstitch on 2015-04-16
Everytime I run **sudo apt-get update** I get these errors and can't figure out how to fix them. I went trough the sources.list file and removed them one by one to see which were the ones giving me the error with no luck.

```
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://download.webmin.com sarge InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty Release.gpg
Get:2 http://security.ubuntu.com trusty-security Release [63.5 kB]
Hit http://us.archive.ubuntu.com trusty Release
Hit http://download.webmin.com sarge Release.gpg
Ign http://ppa.launchpad.net trusty InRelease
Hit http://us.archive.ubuntu.com trusty/main Sources
Ign http://download.opensuse.org  InRelease
Hit http://download.webmin.com sarge Release
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Ign http://ppa.launchpad.net trusty InRelease
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://download.webmin.com sarge/contrib i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Get:3 http://security.ubuntu.com trusty-security/main Sources [78.5 kB]
Hit http://download.opensuse.org  Release.gpg
Ign http://ppa.launchpad.net trusty InRelease
Hit http://update.nzbdrone.com master InRelease
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://update.nzbdrone.com master/main i386 Packages
Get:4 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]
Hit http://download.opensuse.org  Release
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Ign http://ppa.launchpad.net trusty InRelease
Hit http://www.deb-multimedia.org wheezy InRelease
Get:5 http://security.ubuntu.com trusty-security/main i386 Packages [248 kB]
Ign http://ppa.launchpad.net trusty Release.gpg
Hit http://download.opensuse.org  Packages
Hit http://www.deb-multimedia.org wheezy/main i386 Packages
Hit http://ppa.launchpad.net trusty Release.gpg
Hit http://www.deb-multimedia.org wheezy/non-free i386 Packages
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Get:6 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:7 http://ppa.launchpad.net trusty Release.gpg [316 B]
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://ppa.launchpad.net trusty Release.gpg
Ign http://ppa.launchpad.net trusty Release
Ign http://download.webmin.com sarge/contrib Translation-en_US
Hit http://ppa.launchpad.net trusty Release
Ign http://download.webmin.com sarge/contrib Translation-en
Hit http://ppa.launchpad.net trusty Release
Ign http://ppa.launchpad.net trusty Release
Ign http://update.nzbdrone.com master/main Translation-en_US
Hit http://ppa.launchpad.net trusty Release
Ign http://update.nzbdrone.com master/main Translation-en
Hit http://shell.ninthgate.se wheezy InRelease
Hit http://shell.ninthgate.se wheezy/main i386 Packages
Ign http://download.opensuse.org  Translation-en_US
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en
Ign http://download.opensuse.org  Translation-en
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://shell.ninthgate.se wheezy/main Translation-en_US
Ign http://www.deb-multimedia.org wheezy/main Translation-en_US
Ign http://shell.ninthgate.se wheezy/main Translation-en
Ign http://www.deb-multimedia.org wheezy/main Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://www.deb-multimedia.org wheezy/non-free Translation-en_US
Ign http://www.deb-multimedia.org wheezy/non-free Translation-en
[B]Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found[/B]
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Fetched 402 kB in 6s (66.0 kB/s)
[B]W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DF9B28CA252A784
W: Failed to fetch http://ppa.launchpad.net/directhex/monoxide/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.[/B]


```

Here is my /etc/apt/sources.list file:

```
#

# deb cdrom:[Ubuntu-Server 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.3)]/ trusty main restricted

# deb cdrom:[Ubuntu-Server 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.3)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
#deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
#deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
#deb http://security.ubuntu.com/ubuntu trusty-security universe
#deb-src http://security.ubuntu.com/ubuntu trusty-security universe
#deb http://security.ubuntu.com/ubuntu trusty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://download.webmin.com/download/repository sarge contrib
# deb http://ppa.launchpad.net/jcfp/ppa/ubuntu trusty main
deb http://update.nzbdrone.com/repos/apt/debian master main

```

---

### Post by oldos2er on 2015-04-16
PPAs are listed in /etc/apt/sources.list.d/ usually; but you should be able to add the missing key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4DF9B28CA252A784

sudo apt-get update
```

---

### Post by joelstitch on 2015-04-16
Ok, that fixed some but now I still have these:

```
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/directhex/monoxide/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by plucky on 2015-04-17
As oldos2er says 

**PPAs are listed in /etc/apt/sources.list.d/ usually**

Disable the PPA by editing the .list file found in /etc/apt/sources.list.d/

```
ls /etc/apt/sources.list.d/
``` to see if the file is in there.

Good luck

---

### Post by joelstitch on 2015-04-17
Ok I fixed it by removing **directhex-monoxide-trusty.list **and **directhex-monoxide-trusty.list.save** which are from the program **Sonarr (NZBDrone)**. For the Duplicate sources I fixed the file **plex.list** that had it twice. Thanks for the help!

---

