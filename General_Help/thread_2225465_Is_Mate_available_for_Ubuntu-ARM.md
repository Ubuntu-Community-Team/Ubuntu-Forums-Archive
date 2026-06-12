---
title: "Is Mate available for Ubuntu-ARM?"
date: 2014-05-21
forum: General Help
---

### Post by Fallingwater on 2014-05-21
I'm running Ubuntu 13.04 on a Toshiba AC100. It comes with LMDE, which I really don't like, but the others are all heavier on system resources, and with a non-upgradable 512 MB of RAM and a CPU that doesn't exactly scream RAGING POWER, running KDE just doesn't seem like a good idea. I could try XFCE or one of the others, but I really really like Mate (it's my default on every x86 distro I use), so I'd like to install it here as well. I Googled and it seems to be available for Arch ARM, but I couldn't manage to get Arch installed on the AC100 (yes, I did follow the guides, and no, it didn't get me anywhere). No word on whether it can be installed on Ubuntu ARM.

Can it?

---

### Post by grahammechanical on 2014-05-21
I have no experience of any of this but why would in not work? After all it is Linux that has to run on the ARM CPU and not Ubuntu or the desktop environment. If you have ubuntu running on an ARM CPU then any of the applications that come with Ubuntu must surely run.

This is coming up to a year old now

[https://wiki.ubuntu.com/ARM/TEGRA/AC100](https://wiki.ubuntu.com/ARM/TEGRA/AC100)

Question. Have you been able to install any of the applications from the Ubuntu Software Centre? I do not think that those applications are especially coded for ARM CPUs. Sadly, I do not see Mate in the 14.10 Ubuntu Software Centre. Although this disagrees with me.

[http://wiki.mate-desktop.org/download/](http://wiki.mate-desktop.org/download/)

Ah, It is there. I needed to search for mate-desktop-environment. So, if you can get Ubuntu or a flavour of Ubuntu on to that machine then the software centre will install the Mate desktop environment for you.

I think that the image you need is called Lubuntu Desktop Preinstalled armhf+ac100

This is the latest image I could find. It is from 05/02/2014

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/62584/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/62584/downloads)

Regards.

---

### Post by Fallingwater on 2014-05-22
14.10 is not yet available for the AC100. I tried in 14.04, but the instructions don't work - predictably, it can't find the armhf package list in the Mate repository.

---

