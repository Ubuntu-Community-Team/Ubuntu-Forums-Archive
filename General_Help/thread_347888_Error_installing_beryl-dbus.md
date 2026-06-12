---
title: "Error installing beryl-dbus"
date: 2007-01-27
forum: General Help
---

### Post by haani on 2007-01-27
hi when i try to install beryl-dbus i get this error i am using ubuntu 6.10

> haani@haani-laptop:~$ sudo apt-get install beryl-dbus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  beryl-dbus
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.5kB of archives.
After unpacking 102kB of additional disk space will be used.
(Reading database ... 92305 files and directories currently installed.)
Unpacking beryl-dbus (from .../beryl-dbus_0.1.5+svn20070108-r2517+3v1ubuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/beryl-dbus_0.1.5+svn20070108-r2517+3v1ubuntu6_i386.deb (--unpack):
trying to overwrite `/usr/lib/beryl/libdbus.so', which is also in package beryl-plugins
Errors were encountered while processing:
/var/cache/apt/archives/beryl-dbus_0.1.5+svn20070108-r2517+3v1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ingo on 2007-05-15
I get the same error message. Have you managed to get it sorted, haani?

---

### Post by ingo on 2007-05-15
Right, found a solution! I'm running KDE BTW

First download [COLOR=Red][this]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/aquamarine_0.2.0+svn20070118-r2812+3v1ubuntu1_i386.deb")[/COLOR], then install ```
sudo dpkg -i aquamarine_0.2.0+svn20070118-r2812+3v1ubuntu1_i386.deb
``` Finally run ```
sudo apt-get install -f
```and everything should be hunky-dory.

For a full explanation or if you are running the gnome desktop please refer to the third post [COLOR=Red][here]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4046&st=0&sk=t&sd=a&start=50")[/COLOR] and you will be delivered from all pains.

Cheers

Ingo

---

