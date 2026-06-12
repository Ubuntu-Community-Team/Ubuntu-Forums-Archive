---
title: "Repository list after upgrade from 18.04 to 18.10"
date: 2018-10-22
forum: General Help
---

### Post by gottaslay on 2018-10-22
After upgrading, many of the repositories became unchecked. [https://imgur.com/a/vyTrs0g](https://imgur.com/a/vyTrs0g) Should i keep them the way they are or are some of those  still needed?

---

### Post by oldos2er on 2018-10-22
If you've updated to Cosmic you don't want Bionic repositories anymore,  so that's normal. Can you post your sources list? ```
cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/
```

---

### Post by gottaslay on 2018-10-22
```
# deb cdrom:[Ubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725)]/ bionic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic main restricted
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic-updates main restricted
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic universe
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic-updates universe
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic multiverse
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic-updates multiverse
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic-backports main restricted universe multiverse
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) cosmic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) cosmic main
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
```

```
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
graphics-drivers-ubuntu-ppa-bionic.list
graphics-drivers-ubuntu-ppa-bionic.list.distUpgrade
graphics-drivers-ubuntu-ppa-bionic.list.save
lutris.list
lutris.list.save
mikhailnov-ubuntu-pulseeffects-bionic.list
mikhailnov-ubuntu-pulseeffects-bionic.list.distUpgrade
mikhailnov-ubuntu-pulseeffects-bionic.list.save
mikhailnov-ubuntu-pulseeffects-cosmic.list
nilarimogard-ubuntu-webupd8-cosmic.list
nilarimogard-ubuntu-webupd8-cosmic.list.save
peek-developers-ubuntu-stable-bionic.list
peek-developers-ubuntu-stable-bionic.list.distUpgrade
peek-developers-ubuntu-stable-bionic.list.save
peterlevi-ubuntu-ppa-cosmic.list
peterlevi-ubuntu-ppa-cosmic.list.save
steam.list
steam.list.save
teejee2008-ubuntu-ppa-cosmic.list
teejee2008-ubuntu-ppa-cosmic.list.save
ubuntu-wine-ubuntu-ppa-cosmic.list
ubuntu-wine-ubuntu-ppa-cosmic.list.save
webupd8team-ubuntu-java-cosmic.list
webupd8team-ubuntu-java-cosmic.list.save
```

---

