---
title: "Apt-get Error - Cannot install, update or uninstall software"
date: 2007-04-18
forum: General Help
---

### Post by mattmcmanus on 2007-04-18
I haven't been able to install any new programs or run any updates for 4 days now. Update Manger won't open, Synaptic goes to install but then just closes the window and doesnt tell me anything about what happened. .deb all fail on install and give no output why. The only idea I have about what is going on is when I try to run apt-get upgrade it gives this dkpg: parse error. 

```
matt@minibetty:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  automatix2 linux-headers-2.6.20-15 linux-headers-2.6.20-15-generic
  linux-image-2.6.20-15-generic linux-libc-dev linux-source-2.6.20
  update-manager update-manager-core
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/82.4MB of archives.
After unpacking 8192B disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 8302 package `xserver-xorg-video-savage':
 field name `bl' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Anyone have any idea with what is going on?

---

### Post by mattmcmanus on 2007-04-18
It looks like i figure it out. I looked in the available file and the line where it was giving there error was all gobblygook. There about 10 lines of it. I backup the original and removed the lines and all seems to be well. Im not sure what the available file completely entails or if removing those lines means anything but all seems to be well so im happy.

---

