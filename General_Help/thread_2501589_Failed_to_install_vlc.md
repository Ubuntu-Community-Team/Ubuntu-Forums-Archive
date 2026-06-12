---
title: "Failed to install vlc"
date: 2024-10-14
forum: General Help
---

### Post by jimhce on 2024-10-14
Hi,

I used version version 16 version 18 without any issues to install and to run vlc, incredibly failed to install vlc for the version 20.04, I fear the immature of new version, please don't ask me to upate to 22 here are issues:

$ sudo apt update
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease           
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease    
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease
Hit:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal InRelease
Hit:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates InRelease
Hit:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-backports InRelease
Hit:7 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

$ sudo apt install vlc
The following packages have unmet dependencies:
 vlc : Depends: vlc-plugin-base (= 3.0.9.2-1) but it is not going to be installed
       Depends: vlc-plugin-video-output (= 3.0.9.2-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

$ sudo apt install vlc-plugin-base
The following packages have unmet dependencies:
 vlc-plugin-base : Depends: libavcodec58 (>= 7:4.2)
                   Depends: libavformat58 (>= 7:4.2) but it is not going to be installed
                   Depends: libchromaprint1 (>= 1.3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

$ sudo apt install libavcodec58 libavformat58 libchromaprint1
The following packages have unmet dependencies:
 libavcodec58 : Depends: libwebpmux3 (>= 0.6.1-2ubuntu0.20.04.1) but 0.6.1-2 is to be installed
E: Unable to correct problems, you have held broken packages.

$ sudo apt install libwebpmux3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libwebpmux3 is already the newest version (0.6.1-2).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

So the libwebpmux3 has already been the newest version, what's going on for version 20 apt?

Thank you.

Kind regards,

BJ

---

### Post by howefield on 2024-10-14
Not a feedback post, so thread moved to the "*General Help*" forum.

---

### Post by grahammechanical on 2024-10-14
If an application cannot be installed because it has dependences that are not going to be installed, then there is no point in trying to installed those packages that the application depends upon. They are simply not going to be installed. 

Those packages that VLC depends upon are in the Universe repository. Do you have the Universe repository enabled on your system?

Here is one tutorial

[https://itsfoss.com/install-latest-vlc/](https://itsfoss.com/install-latest-vlc/)

Regards

---

### Post by jimhce on 2024-10-16
[QUOTE=grahammechanical;14209339Those packages that VLC depends upon are in the Universe repository. Do you have the Universe repository enabled on your system?
Regards[/QUOTE]

Yes, 

$ sudo add-apt-repository universe
'universe' distribution component is already enabled for all sources.

$ cat /etc/apt/sources.list
.............
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal main universe restricted multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal-updates universe
..........

Thank you very much

Kind regards

BJ

---

