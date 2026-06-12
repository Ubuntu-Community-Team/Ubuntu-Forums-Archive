---
title: "[SOLVED] Libc6 Dependency Error"
date: 2008-01-28
forum: General Help
---

### Post by SoulSmasher on 2008-01-28
hi, i searched in forums for similar threads, and couldn't find a solution to my problem. if solved, sorry for posting :(

ive this issue about package libc6,

@synaptic package manager, main libc6 version is 2.7-5ubuntu2, but other libc6 dependent packages are 2.6.1-1ubuntu10

thats why when i try to install some packages that are dependent to libc6 gives errors..
i.e, when i try to install build-essential from konsole, i get this command:
```
arda@arda-laptop:~/Desktop$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.1.1) but it is not going to be installed
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu9) but 2.7-5ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arda@arda-laptop:~/Desktop$

```

and when i try to install with -f parameter i get this:
```
arda@arda-laptop:~/Desktop$ sudo apt-get -f install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.1.1) but it is not going to be installed
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu9) but 2.7-5ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arda@arda-laptop:~/Desktop$

``` 

ok. i get g++ etc from packages.ubuntu.com, download .deb, then use this command to install:
```
sudo dpkg --force-depends -i <packagename.deb>
```
it works , but notifier gives error as it has broken packages..

the main issue is: how do i fix this issue, i mean, either how update package versions of libc6, from synaptic? i know, i cant :) but is there an updated version ? so it understands new versions and doesn't issue dependency and broken packages ?
or how do i downgrade libc6 to 2.6.1 ?

ps: i'm using ftp.stud.etc etc (one germany server) for package downloading..

thanks for any further help
Sincerally
Arda

---

### Post by PmDematagoda on 2008-01-28
Could you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by SoulSmasher on 2008-01-28
thanks for the interest :), here's the output

```


arda@arda-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://ftp.stw-bonn.de/ubuntu/ gutsy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.stw-bonn.de/ubuntu/ gutsy main restricted
deb-src http://ftp.stw-bonn.de/ubuntu/ gutsy main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.stw-bonn.de/ubuntu/ gutsy-updates main restricted
deb-src http://ftp.stw-bonn.de/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ftp.stw-bonn.de/ubuntu/ gutsy universe
deb http://ftp.stw-bonn.de/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.stw-bonn.de/ubuntu/ gutsy multiverse
deb http://ftp.stw-bonn.de/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://tr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://tr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://ftp.stw-bonn.de/ubuntu/ gutsy-security main restricted
deb-src http://ftp.stw-bonn.de/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://ftp.stw-bonn.de/ubuntu/ gutsy-security universe
deb http://ftp.stw-bonn.de/ubuntu/ gutsy-security multiverse
arda@arda-laptop:~$                  
```

---

### Post by zvacet on 2008-01-28
```
sudo apt-get -f install
```

---

### Post by SoulSmasher on 2008-01-28
> **zvacet said:**
> ```
sudo apt-get -f install
```

it does nothing..
this is its output..
```

[sudo] password for arda:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-resource-dev libxkbui-dev libxtrap-dev libxaw-headers libsm-dev
  libxmuu-dev libice-dev libglitz-glx1 libxaw7-dev x11proto-xext-dev
  libatk1.0-dev x11proto-fonts-dev x11proto-xf86dga-dev x11proto-kb-dev
  libglib2.0-dev x11proto-gl-dev xserver-xorg-dev libxv-dev
  x11proto-xf86misc-dev x11proto-xinerama-dev libsvga1 x11proto-bigreqs-dev
  libxkbui1 x11proto-render-dev x11proto-video-dev libxi-dev libxmu-headers
  libxrender-dev mesa-common-dev libxxf86dga-dev libxdmcp-dev linux-libc-dev
  libdmx-dev libxevie-dev libxxf86misc-dev x11proto-trap-dev
  x11proto-record-dev libfs-dev x11proto-composite-dev xtrans-dev
  x11proto-core-dev libxcursor-dev x11proto-dmx-dev libcdio-cdda0
  x11proto-scrnsaver-dev x11proto-xf86bigfont-dev x11proto-randr-dev
  x11proto-damage-dev libxt-dev libxmu-dev libxext-dev libxdamage-dev
  libglitz1 libraw1394-dev x11proto-input-dev libxpm-dev x11proto-fixes-dev
  libxau-dev libxcomposite-dev libcdio-paranoia0 libxrandr-dev
  x11proto-evie-dev x11proto-xf86vidmode-dev libxvmc-dev libx11-dev
  libxxf86vm-dev libxres-dev libxfixes-dev libswt3.2-gtk-jni libavutil-dev
  x11proto-xcmisc-dev libxinerama-dev x11proto-xf86dri-dev
  x11proto-fontcache-dev libgsm1-dev libxss-dev libxtst-dev libxkbfile-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
arda@arda-laptop:~$   
```


im really confused :S

---

### Post by zvacet on 2008-01-28
System>administration>software sources>chek all boxes under Ubuntu software and under update tab.Reload.Select **main server**.Try to install again.

---

### Post by SoulSmasher on 2008-01-29
i tried with main server. no hope

then i made my pc ready for format :) after that i downgraded libc6 to 2.6.1-1ubuntu10, after reestart, pc didn't run properly, only a black screen, even there was no login window

then i formatted, now everything works fine..

i think that package update came with one of th getdeb.net's packages..

thank you for help btw :)

---

