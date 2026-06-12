---
title: "Cant uninstall ndiswrapper"
date: 2007-05-23
forum: General Help
---

### Post by Staudie on 2007-05-23
I want to upgrade my ndiswrapper to the lastest version but Im unable to remove it.

[COD]staudie@MYTHTV:~$ ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 
staudie@MYTHTV:~$[/CODE]

```
staudie@MYTHTV:~$ sudo apt-cache search ndiswrapper
linux-image-2.6.20-15-386 - Linux kernel image for version 2.6.20 on i386
linux-image-2.6.20-15-generic - Linux kernel image for version 2.6.20 on x86/x86_64
linux-image-2.6.20-15-server - Linux kernel image for version 2.6.20 on x86/x86_64
linux-image-2.6.20-15-server-bigiron - Linux kernel image for version 2.6.20 on BigIron Server Equipment
ndiswrapper-common - Common scripts required to use the utilities for ndiswrapper
ndiswrapper-utils-1.9 - Userspace utilities for the ndiswrapper linux kernel module
linux-image-2.6.20-15-lowlatency - Linux kernel image for version 2.6.20 on x86/x86_64
ndisgtk - graphical frontend for ndiswrapper (installation of Windows WiFi drivers)
ndiswrapper-source - Source for the ndiswrapper linux kernel module
staudie@MYTHTV:~$
```

```
staudie@MYTHTV:~$ sudo apt-get remove ndiswrapper-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
staudie@MYTHTV:~$
```

```
staudie@MYTHTV:~$ sudo make uninstall ndiswrapper-source
make: *** No rule to make target `uninstall'.  Stop.
staudie@MYTHTV:~$
```

What do I need to do to remove this so I can install 1.44???

Thanks for the Help
-Staudie

---

### Post by bmartin on 2007-05-23
Try **sudo apt-get remove ndiswrapper-common**

---

### Post by Staudie on 2007-05-23
Ive tried:

```
sudo apt-get remove ndiswrapper-common
```
```
sudo apt-get remove ndiswrapper-source
```
```
sudo apt-get remove ndiswrapper-utils-1.9
```

all of which give me the same response

```
staudie@MYTHTV:~$ sudo apt-get remove ndiswrapper-******
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-****** is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
staudie@MYTHTV:~$
```

-Staudie

---

