---
title: "Ubuntu 16.10 Update problem (some repository yakkety release does not have Release )"
date: 2018-01-25
forum: General Help
---

### Post by acrontias on 2018-01-25
I try to update a system (apt-get update), but I got some errors. 

Concretely (main error):
```

E:The repository 'http://archive.ubuntu.com/ubuntu yakkety Release' does  not have a Release file., W:Updating from such a repository can't be  done securely, and is therefore disabled by default., W:See  apt-secure(8) manpage for repository creation and user configuration  details., E:The repository 'http://archive.ubuntu.com/ubuntu  yakkety-updates Release' does not have a Release file., W:Updating from  such a repository can't be done securely, and is therefore disabled by  default., W:See apt-secure(8) manpage for repository creation and user  configuration details., E:The repository  'http://archive.ubuntu.com/ubuntu yakkety-security Release' does not  have a Release file.

```

My Ubuntu version:[INDENT]Description:    Ubuntu 16.10
Codename:    yakkety
[/INDENT]

I tried a lot of solutions found in different threads and different sources, such as :
sudo apt-get autoclean 
sudo apt-get clean
sudo apt-get update

I disabled all PPA's from "Other software" of "Software and Updates" (just in case..).

And also, I commented a pair of lines of sources.list file (just to try):
####deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-backports main universe restricted multiverse
####deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety partner

... but the main error remains (see "main error" on top) ... 

When I try to : sudo apt-get update

I got this :
```

...
Ign:79 http://archive.ubuntu.com/ubuntu yakkety-security/universe amd64 Packages
Ign:80 http://archive.ubuntu.com/ubuntu yakkety-security/universe i386 Packages
Ign:81 http://archive.ubuntu.com/ubuntu yakkety-security/universe all Packages
Reading package lists... Done
W: The repository 'http://archive.ubuntu.com/ubuntu yakkety Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu yakkety-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu yakkety-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/yakkety/main/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]
E: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/yakkety-updates/main/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]
E: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/yakkety-security/main/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Finally this are my sources.list file :
```

$ cat sources.list
# deb cdrom:[Ubuntu 16.10 _Yakkety Yak_ - Release amd64 (20161012.2)]/ yakkety main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu yakkety main universe restricted multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ yakkety main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu yakkety-updates main universe restricted multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ yakkety-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://es.archive.ubuntu.com/ubuntu/ yakkety universe
# deb-src http://es.archive.ubuntu.com/ubuntu/ yakkety-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://es.archive.ubuntu.com/ubuntu/ yakkety multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ yakkety-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
####deb http://archive.ubuntu.com/ubuntu yakkety-backports main universe restricted multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
####deb http://archive.canonical.com/ubuntu yakkety partner
deb-src http://archive.canonical.com/ubuntu yakkety partner

deb http://archive.ubuntu.com/ubuntu yakkety-security main universe restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu yakkety-security main restricted
# deb-src http://security.ubuntu.com/ubuntu yakkety-security universe
# deb-src http://security.ubuntu.com/ubuntu yakkety-security multiverse
# deb https://cli-assets.heroku.com/branches/stable/apt ./
# deb-src https://cli-assets.heroku.com/branches/stable/apt ./


```

Any ideas? Thanks in advance!

---

### Post by howefield on 2018-01-25
Ubuntu has long passed end of life and the repositories have been moved to the old-releases archive.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Best to upgrade to a supported release. 16.04 is supported until April 2021.

---

### Post by Impavidus on 2018-01-25
As 17.04 has reached end of life too, I suggest you don't try to upgrade. Get a fresh install of 16.04 (yes, that's kind of downgrading) or 17.10.

---

