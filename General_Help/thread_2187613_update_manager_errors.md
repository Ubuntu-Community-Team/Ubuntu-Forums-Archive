---
title: "update manager errors"
date: 2013-11-13
forum: General Help
---

### Post by vbdanl-yahoo on 2013-11-13
hi all,
i recently added a new nvidia gt610 graphics card and second monitor.  both seem to be working fine.
since adding them, i now get errors from update mgr.  have read lots of threads, tried clean, fix-broken, and autoremove.. nothing has worked.. i could use some help.
my goal is to be able to dial into work via our vpn and remote desktop using the dual monitors, which is the setup i have at work.
i have installed NetExtender, and it seems to work.  I have not been able to get a remote desktop using remmina after connecting with NetExtender.
Sorry, i think this is really 2 problems, and i am not sure if i should create 2 threads, or keep this in one..
For the update mgr problem i am having, here is what comes back from sudo apt-get upgrade
```
:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libgl1-mesa-dri linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-geode xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.

```
and here is what is in sources.list
```
:/etc/apt$ cat sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```
thanks for any help.

---

### Post by fantab on 2013-11-13
What happens when you do:

```
sudo apt-get update
sudo apt-get -f install
```

---

### Post by plucky on 2013-11-13
> **fantab said:**
> What happens when you do:

```
sudo apt-get update
sudo apt-get -f install
```

Or ```
sudo apt-get dist-upgrade
```

---

### Post by philinux on 2013-11-13
dist-upgrade will sort it.

---

### Post by vbdanl-yahoo on 2013-11-13
i had already tried the update and -f install.. they did not work.. still said 30 packages have been kept back.
the dist-upgrade looks to be working..
thanks for all your help !!
now if i can get the rdp to work, i will be in great shape.

---

