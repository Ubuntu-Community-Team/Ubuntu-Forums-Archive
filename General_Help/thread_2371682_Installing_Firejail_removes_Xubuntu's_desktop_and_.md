---
title: "Installing Firejail removes Xubuntu's desktop and core?"
date: 2017-09-17
forum: General Help
---

### Post by ardouronerous on 2017-09-17
I've tried to install Firejail via Synaptic, but it tries to remove Xubuntu's desktop and core, so I cancelled it, is this normal?
[ATTACH=CONFIG]276760[/ATTACH]

I'm running Xubuntu 16.04 LTS 32-bit.

---

### Post by oldos2er on 2017-09-17
Can't see everything in that window. Can you post all the output of ```
sudo apt update; sudo apt install -s firejail
``` The -s switch means simulation, nothing will actually be installed or removed.

---

### Post by ardouronerous on 2017-09-17
```
~$ sudo apt update; sudo apt install -s firejail
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]       
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Ign:4 http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_16.04  InRelease
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:6 http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_16.04  Release
Hit:7 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease    
Get:8 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]     
Hit:10 http://ppa.launchpad.net/openmw/openmw-daily/ubuntu xenial InRelease    
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe i386 DEP-11 Metadata [48.9 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [64.2 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main i386 DEP-11 Metadata [60.0 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [57.0 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 DEP-11 Metadata [7,060 B]
Get:16 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 DEP-11 Metadata [172 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [221 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 DEP-11 Metadata [305 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [213 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-backports/universe i386 DEP-11 Metadata [5,136 B]
Get:21 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 DEP-11 Metadata [3,324 B]
Fetched 1,463 kB in 9s (152 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbinio1v5 libqt5printsupport5 libxfont2 linux-headers-4.10.0-27
  linux-headers-4.10.0-27-generic linux-headers-4.10.0-28
  linux-headers-4.10.0-28-generic linux-headers-4.10.0-30
  linux-headers-4.10.0-30-generic linux-headers-4.4.0-77
  linux-headers-4.4.0-77-generic linux-headers-4.4.0-78
  linux-headers-4.4.0-78-generic linux-headers-4.4.0-79
  linux-headers-4.4.0-79-generic linux-headers-4.4.0-87
  linux-headers-4.4.0-87-generic linux-headers-4.4.0-89
  linux-headers-4.4.0-89-generic linux-headers-4.4.0-91
  linux-headers-4.4.0-91-generic linux-headers-4.4.0-92
  linux-headers-4.4.0-92-generic linux-headers-4.8.0-54
  linux-headers-4.8.0-54-generic linux-headers-4.8.0-56
  linux-headers-4.8.0-56-generic linux-headers-4.8.0-58
  linux-headers-4.8.0-58-generic linux-image-4.10.0-27-generic
  linux-image-4.10.0-28-generic linux-image-4.10.0-30-generic
  linux-image-4.4.0-77-generic linux-image-4.4.0-78-generic
  linux-image-4.4.0-79-generic linux-image-4.4.0-87-generic
  linux-image-4.4.0-89-generic linux-image-4.4.0-91-generic
  linux-image-4.4.0-92-generic linux-image-4.8.0-54-generic
  linux-image-4.8.0-56-generic linux-image-4.8.0-58-generic
  linux-image-extra-4.10.0-27-generic linux-image-extra-4.10.0-28-generic
  linux-image-extra-4.10.0-30-generic linux-image-extra-4.4.0-77-generic
  linux-image-extra-4.4.0-78-generic linux-image-extra-4.4.0-79-generic
  linux-image-extra-4.4.0-87-generic linux-image-extra-4.4.0-89-generic
  linux-image-extra-4.4.0-91-generic linux-image-extra-4.4.0-92-generic
  linux-image-extra-4.8.0-54-generic linux-image-extra-4.8.0-56-generic
  linux-image-extra-4.8.0-58-generic xserver-xorg-core-hwe-16.04
  xserver-xorg-input-all-hwe-16.04 xserver-xorg-input-evdev-hwe-16.04
  xserver-xorg-input-synaptics-hwe-16.04 xserver-xorg-input-wacom-hwe-16.04
  xserver-xorg-legacy-hwe-16.04 xserver-xorg-video-all-hwe-16.04
  xserver-xorg-video-amdgpu-hwe-16.04 xserver-xorg-video-ati-hwe-16.04
  xserver-xorg-video-fbdev-hwe-16.04 xserver-xorg-video-intel-hwe-16.04
  xserver-xorg-video-nouveau-hwe-16.04 xserver-xorg-video-qxl-hwe-16.04
  xserver-xorg-video-radeon-hwe-16.04 xserver-xorg-video-vesa-hwe-16.04
  xserver-xorg-video-vmware-hwe-16.04
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  python-gi-cairo ssh-askpass
Recommended packages:
  xpra | xserver-xephyr
The following packages will be REMOVED:
  xorg xserver-xorg-hwe-16.04 xubuntu-core xubuntu-desktop
The following NEW packages will be installed:
  firejail python-gi-cairo ssh-askpass
0 upgraded, 3 newly installed, 4 to remove and 0 not upgraded.
Remv xubuntu-desktop [2.206]
Remv xubuntu-core [2.206]
Remv xorg [1:7.7+13ubuntu3]
Remv xserver-xorg-hwe-16.04 [1:7.7+16ubuntu3~16.04.1]
Inst firejail (1:0.9.44.10-1 home:stevenpusser:download.opensuse.org [i386])
Inst python-gi-cairo (3.20.0-0ubuntu1 Ubuntu:16.04/xenial [i386])
Inst ssh-askpass (1:1.2.4.1-9 Ubuntu:16.04/xenial [i386])
Conf firejail (1:0.9.44.10-1 home:stevenpusser:download.opensuse.org [i386])
Conf python-gi-cairo (3.20.0-0ubuntu1 Ubuntu:16.04/xenial [i386])
Conf ssh-askpass (1:1.2.4.1-9 Ubuntu:16.04/xenial [i386])
```

---

### Post by oldos2er on 2017-09-17
You've got an awful lot of packages waiting to be autoremoved, some of which are xorg related. Just for comparison here are my results on Xubuntu 17.10: ```
sudo apt install -s firejail
[sudo] password for ann:        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcc-6-base libblas-common libgfortran3
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  firejail-profiles freeglut3 libgtkglext1 python-dbus python-gi python-gi-cairo python-gtkglext1
  python-lz4 python-lzo python-olefile python-opengl python-pil python-rencode ssh-askpass xpra
  xserver-xorg-input-void xserver-xorg-video-dummy
Suggested packages:
  python-dbus-dbg python-dbus-doc python-tk libgle3 python-pil-doc python-pil-dbg openssh-server
  python-pyopencl python-gst-1.0 python-avahi python-netifaces cups-pdf python-cups python-opencv
  v4l2loopback-dkms python-yaml
The following NEW packages will be installed:
  firejail firejail-profiles freeglut3 libgtkglext1 python-dbus python-gi python-gi-cairo
  python-gtkglext1 python-lz4 python-lzo python-olefile python-opengl python-pil python-rencode
  ssh-askpass xpra xserver-xorg-input-void xserver-xorg-video-dummy
0 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Inst firejail (0.9.48-2 Ubuntu:17.10/artful [amd64])
Inst firejail-profiles (0.9.48-2 Ubuntu:17.10/artful [all])
Inst freeglut3 (2.8.1-3 Ubuntu:17.10/artful [amd64])
Inst libgtkglext1 (1.2.0-7 Ubuntu:17.10/artful [amd64])
Inst python-dbus (1.2.4-1build3 Ubuntu:17.10/artful [amd64])
Inst python-gi (3.24.1-2build1 Ubuntu:17.10/artful [amd64])
Inst python-gi-cairo (3.24.1-2build1 Ubuntu:17.10/artful [amd64])
Inst python-lz4 (0.8.2+dfsg-2build2 Ubuntu:17.10/artful [amd64])
Inst python-lzo (1.08-1 Ubuntu:17.10/artful [amd64])
Inst python-olefile (0.44-1 Ubuntu:17.10/artful [all])
Inst python-opengl (3.1.0+dfsg-1 Ubuntu:17.10/artful [all])
Inst python-pil (4.1.1-3build2 Ubuntu:17.10/artful [amd64])
Inst python-rencode (1.0.5-1build2 Ubuntu:17.10/artful [amd64])
Inst ssh-askpass (1:1.2.4.1-9 Ubuntu:17.10/artful [amd64])
Inst xserver-xorg-input-void (1:1.4.1-1build3 Ubuntu:17.10/artful [amd64])
Inst xserver-xorg-video-dummy (1:0.3.8-1build1 Ubuntu:17.10/artful [amd64])
Inst xpra (0.17.6+dfsg-1build1 Ubuntu:17.10/artful [amd64])
Inst python-gtkglext1 (1.1.0-9.1 Ubuntu:17.10/artful [amd64])
Conf firejail (0.9.48-2 Ubuntu:17.10/artful [amd64])
Conf firejail-profiles (0.9.48-2 Ubuntu:17.10/artful [all])
Conf freeglut3 (2.8.1-3 Ubuntu:17.10/artful [amd64])
Conf libgtkglext1 (1.2.0-7 Ubuntu:17.10/artful [amd64])
Conf python-dbus (1.2.4-1build3 Ubuntu:17.10/artful [amd64])
Conf python-gi (3.24.1-2build1 Ubuntu:17.10/artful [amd64])
Conf python-gi-cairo (3.24.1-2build1 Ubuntu:17.10/artful [amd64])
Conf python-lz4 (0.8.2+dfsg-2build2 Ubuntu:17.10/artful [amd64])
Conf python-lzo (1.08-1 Ubuntu:17.10/artful [amd64])
Conf python-olefile (0.44-1 Ubuntu:17.10/artful [all])
Conf python-opengl (3.1.0+dfsg-1 Ubuntu:17.10/artful [all])
Conf python-pil (4.1.1-3build2 Ubuntu:17.10/artful [amd64])
Conf python-rencode (1.0.5-1build2 Ubuntu:17.10/artful [amd64])
Conf ssh-askpass (1:1.2.4.1-9 Ubuntu:17.10/artful [amd64])
Conf xserver-xorg-input-void (1:1.4.1-1build3 Ubuntu:17.10/artful [amd64])
Conf xserver-xorg-video-dummy (1:0.3.8-1build1 Ubuntu:17.10/artful [amd64])
Conf xpra (0.17.6+dfsg-1build1 Ubuntu:17.10/artful [amd64])
Conf python-gtkglext1 (1.1.0-9.1 Ubuntu:17.10/artful [amd64])
```

---

### Post by ardouronerous on 2017-09-17
It looks like the firejail that is being installed is from this repo: [http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_16.04](http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_16.04)

I'm using Pale Moon as my web browser and it comes from that repo.

---

### Post by oldos2er on 2017-09-17
I don't know anything about that repo, but you could try disabling it, then rerun the update and simulation command.

---

### Post by ardouronerous on 2017-09-17
I tried it, it works, but a few issues.

The problem I have with this is, I need to enable the repo afterwards or I don't get the latest updates to Pale Moon, and it's asking me to upgrade Firejail, since the version in Pale Moon's repos is higher than the one available in 16.04's repos.

It's cool.
I think I'll try sticking with AppArmor instead.

Thanks for the help!

---

### Post by again? on 2017-09-17
You don't need to add the repo for updates.
You can use the [Pale Moon for Linux Installer]("http://linux.palemoon.org/download/installer/") to check and install updates.

---

### Post by ardouronerous on 2017-09-17
The problem I have with the installer is that I have to manually check for updates myself, I'd rather take advantage of the autoupdate feature of Ubuntu for this, unless there's a way to cronjob Pale Moon's updates?

I've also read that's there's a way to pin installs from repos, where you can choose what applications you want from the repos.

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

But I don't understand how to do this with [http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_16.04](http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_16.04)

---

### Post by vasa1 on 2017-09-17
I saw something similar to what was reported in the first post when I tried to install firejail from a ppa on or around 3 July 2017. In other words, I wanted a version newer than in the standard repo:```
$ sudo apt-get install firejail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  firejail-profiles python-cairo python-gi python-gi-cairo
Recommended packages:
  xpra | xserver-xephyr | xvfb
The following packages will be REMOVED:
  xorg xserver-xorg-hwe-16.04
The following NEW packages will be installed:
  firejail firejail-profiles python-cairo python-gi python-gi-cairo
0 upgraded, 5 newly installed, 2 to remove and 0 not upgraded.
Need to get 504 kB of archives.
After this operation, 1,936 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```

---

### Post by ardouronerous on 2017-09-17
Is this a bug?
Wouldn't the removal of xorg and xserver-xorg-hwe-16.04 cause system problems?

---

### Post by vasa1 on 2017-09-17
Well, since I tried to install from a ppa, it's more *caveat emptor* than normal.

---

