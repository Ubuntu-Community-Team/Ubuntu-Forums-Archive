---
title: "Problem uninstalling  pulseaudio."
date: 2013-03-09
forum: General Help
---

### Post by arroy_0209 on 2013-03-09
I am using ubuntu 12.04. I do not use pulse audio but keep getting update notofications. To stop these I decided to uninstall pulseaudio and used the command: ```
sudo apt-get remove pulseaudio
``` and planned to use command ```
sudo apt-get autoremove
``` after that. After the first command, the response was:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libpulse0
The following packages will be REMOVED:
  indicator-sound libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-x11 ubuntu-desktop
The following packages will be upgraded:
  libpulse0
1 upgraded, 0 newly installed, 8 to remove and 42 not upgraded.
Need to get 279 kB of archives.
After this operation, 4,537 kB disk space will be freed.
Do you want to continue [Y/n]?

```
My response was 'Y' and the result was:
```

Err http://archive.ubuntu.com/ubuntu/ precise-updates/main libpulse0 i386 1:1.1-0ubuntu15.2
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_1.1-0ubuntu15.2_i386.deb  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
I admit at that time internet was disconnected but I never imagined that in order to remove a program, I needed to be connected to internet. My doubt is, is it compulsory to stay connected to internet to uninstall pulseaudio?

---

### Post by 3rdalbum on 2013-03-09
Look closer at what is being upgraded.

I sure hope you know what you are doing. Removing the sound system will usually leave you without any sound. If this is not what you want to do, then leave Pulseaudio on your system.

---

### Post by oldos2er on 2013-03-09
[FONT=arial]APT always expects an internet connection.

>  [COLOR=#000000]1 upgraded, 0 newly installed, 8 to remove and 42 not upgraded.[/COLOR]

I think you should run the upgrades before removing anything.[/FONT]

---

### Post by tartalo on 2013-03-09
> **3rdalbum said:**
> Removing the sound system will usually leave you without any sound. If this is not what you want to do, then leave Pulseaudio on your system.

You will still have sound after removing Pulseaudio, ALSA works fine.

---

