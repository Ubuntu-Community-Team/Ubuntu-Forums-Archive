---
title: "modprobe: FATAL: Module mach64 not found.  14.04.1.  12.04 worked great"
date: 2014-08-25
forum: General Help
---

### Post by Joanne_Homier on 2014-08-25
modprobe: FATAL: Module mach64 not found.  14.04.1.  12.04 worked great

Old ati laptop.  ATI Rage Mobility AGP 2x series (rev 64).  Ubuntu server 14.04.1 with openbox, firefox, xorg meta package.  XFE file manager.  Installed all dependencies that I could find.  Used Aptitude.

12.04 same thing and worked great.

Backtrace points to mach64.

---

### Post by ibjsb4 on 2014-08-26
This the package?

[http://packages.ubuntu.com/trusty/xserver-xorg-video-mach64](http://packages.ubuntu.com/trusty/xserver-xorg-video-mach64)

---

### Post by MAFoElffen on 2014-09-29
Same problem. Server 14.04, with a minimal X install (openbox, etc...) and package xserver-xorg-video-mach64 was installed and is the newest version. 

I just upgraded that server from 12.04LTS Server. Before the upgrade, it had worked fine using *startx* to boot an instance of X for doing maintenance. 

Did a release upgrade (today) to 14.04 and it's now broke. XLog has that same exact message. Diving into it right now to check it out (see why it broke). 

I'll follow this thread to see if someone beats me to a solution. If I find something out that fixes mine, I'll post my resolution here.

EDIT-- Added as a Bug here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mach64/+bug/1375511](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mach64/+bug/1375511)

---

### Post by MAFoElffen on 2014-10-01
I asked them to close out my bug. My last post at launchpad explains what I did to resolve it. When I installed origianlly, I used to do minimal X installs using an aptitude flag --without recommends so it would not install full packages with pieces that were not needed. Seems there is some change from 12.04.3 to 14.04.1, were there is probably a changed dependency somehwere...

I removed X packages back into removing the XServer core... down to the commandline. Then used the script I uploaded there to reinstall it. Same packages install, but without the "--withoutrecommends" switch on the command. A bit heavier, but works fine now.

---

