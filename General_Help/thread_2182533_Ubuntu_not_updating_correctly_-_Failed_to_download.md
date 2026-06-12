---
title: "Ubuntu not updating correctly - Failed to download packages check internet connection"
date: 2013-10-21
forum: General Help
---

### Post by Sinfieldd on 2013-10-21
Hi, 

I'm having an issue with Ubuntu 12.04 at the moment whereby it takes a while to log in because it is opening update manager (96 updates) and when I try to update it, I am greeted with the message 'Failed to download packages' and 'check your internet connection'.

I am definitely connected to the internet, as I am posting this now.

I've posted the details below:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.14_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.14_amd64.deb) 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.16~exp12ubuntu10.14_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.16~exp12ubuntu10.14_amd64.deb) 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.4_0.8.16~exp12ubuntu10.14_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.4_0.8.16~exp12ubuntu10.14_amd64.deb) 404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_30.0.1599.66-1_amd64.deb](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_30.0.1599.66-1_amd64.deb) 404  Not Found [IP: 173.194.41.168 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool](http://gb.archive.ubuntu.com/ubuntu/pool)

Does anybody know what the remedy for this is?

Many thanks.

---

### Post by philinux on 2013-10-21
Can you post your sources list.
From a terminal. 
cat /etc/apt/sources.list

---

### Post by Sinfieldd on 2013-10-21
deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by philinux on 2013-10-21
]Ok. From terminal again

sudo apt-get update && sudo apt-get upgrade

Post back any errors.

---

### Post by Sinfieldd on 2013-10-21
It seemed to work from terminal, the only thing I could pick out as an error was this:

W: Duplicate sources.list entry cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.2%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20130213)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.2%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20130213)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


I would run sudo apt-get update again but it would just show the same thing once it was done.

---

### Post by Sinfieldd on 2013-10-21
Funnily enough it's working on update manager now..

---

### Post by philinux on 2013-10-21
Yes you have a duplicate for the cdrom. I would remove one from software sources.

---

