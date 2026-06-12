---
title: "Dependency issues with nvidia-tegra package"
date: 2014-05-22
forum: General Help
---

### Post by Fallingwater on 2014-05-22
I'm trying to get Lubuntu 14.04 (armhf version as downloaded from [here]("http://ftp.heanet.ie/mirrors/ubuntu-cdimage/lubuntu/daily-preinstalled/current/")) running on a Toshiba AC100, which involves installing the proprietary drivers from nVidia.

Now, previous versions of Lubuntu for the AC100 had the nvidia-tegra package easily installable in preferences->software&updates, but if I try it now it says no drivers available. So I went looking for the nvidia-tegra deb for Trusty and found it [here]("https://launchpad.net/ubuntu/trusty/armhf/nvidia-tegra/16.3-0ubuntu2"). Problem is, if I try to install it it complains about a "xorg-video-abi-14" missing dependency. 

If I try apt-get install xorg-video-abi-14 it says it's unavailable but referred to by another package. I went looking and found [this]("https://launchpad.net/ubuntu/trusty/amd64/xserver-xorg-core/2:1.14.5-1ubuntu1") according to which it's supposed to be provided by xserver-xorg-core, but that's for amd64 systems and in any case the version of xserver-xorg-core I have in my install (2:1.15.1-0ubuntu2) doesn't seem to provide it.

Getting the proprietary driver running is paramount, as the graphics are really slow on the OSS one, to the point I'll downgrade to 13.10 or earlier before making do without. I'd much rather get it working in 14.04 though, so what do I do?

---

