---
title: "Media change: please insert the disc labeled 'Ubuntu 13.04 _Raring Ringtail_ - Releas"
date: 2013-09-05
forum: General Help
---

### Post by frederik-f on 2013-09-05
I'm trying to install the 'Required packages' from Android Open Source Project.

After typing: 
[PHP]sudo apt-get install git-core gnupg flex bison gperf \
build-essential zip curl zlib1g-dev zlib1g-dev:i386 \
libc6-dev lib32ncurses5-dev ia32-libs x11proto-core-dev \
libx11-dev:i386 libreadline6-dev:i386 lib32z1-dev \
libgl1-mesa-glx:i386 libgl1-mesa-dev g++-multilib \
mingw32 tofrodos python-markdown libxml2-utils \
xsltproc readline-common libreadline6-dev libreadline6 \
lib32readline-gplv2-dev libncurses5-dev lib32readline5 \
lib32readline6 libreadline-dev libreadline6-dev:i386 \
libreadline6:i386 bzip2 libbz2-dev libbz2-1.0 vim \
libghc-bzlib-dev lib32bz2-dev libsdl1.2-dev libesd0-dev \
squashfs-tools pngcrush schedtool libwxgtk2.8-dev python[/PHP]
I get this error:

Media change: please insert the disc labeled
 'Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)'
in the drive '/cdrom/' and press enter

What should I do? I used an USB when I installed Ubuntu 13.04 and don't have a disc. Should I make one? And why does it ask for that?

---

### Post by steeldriver on 2013-09-05
It probably just means that (for whatever reason) the original CDROM sources didn't get commented out in your /etc/apt/sources.list file after installation - you can fix that by opening Software Center and then going to the 'Edit' menu --> 'Software sources' and making sure the CDROM checkbox is deselected. Or open your /etc/apt/sources.list file and edit it directly, putting comment characters (#) in front of the 'deb cdrom' lines (needs sudo or gksudo as appropriate, depending what editor you use). Then update your sources with

```
sudo apt-get update
```

and try again.

---

