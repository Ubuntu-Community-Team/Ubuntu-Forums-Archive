---
title: "libc upgrade woes"
date: 2007-02-03
forum: General Help
---

### Post by spbkaizo on 2007-02-03
Hi there,

I'm having trouble trying to upgrade my xubuntu 6.10 machine, with libc.  Here's the error messages:

First up, an apt-get upgrade:

```

root@tachikoma:/home/simonb# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  app-install-data-commercial gnome-applets gnome-applets-data gnome-applets-dev gnome-netstatus-applet gnome-panel
  gnome-panel-data libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtk2.0-dev libpanel-applet2-0 libsoup2.2-8
  libtotem-plparser1 libvlc0 libvolumeid0 libwxbase2.6-0 libwxgtk2.6-0 mozilla-plugin-vlc system-tools-backends udev vlc
  vlc-nox vlc-plugin-alsa volumeid wxvlc xpdf xpdf-common xpdf-reader xpdf-utils xubuntu-system-tools
31 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/32.9MB of archives.
After unpacking 4096B disk space will be freed.
Do you want to continue [Y/n]? 
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done       
Extract templates from packages: 100%
Preconfiguring packages ...
Setting up libc6 (2.4-1ubuntu12.3) ...
Segmentation fault
dpkg: error processing libc6 (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 libc6
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Then, apt-get -f install
```

root@tachikoma:/home/simonb# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libc6 (2.4-1ubuntu12.3) ...
Segmentation fault
dpkg: error processing libc6 (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libc6-i686:
 libc6-i686 depends on libc6 (= 2.4-1ubuntu12.3); however:
  Package libc6 is not configured yet.
dpkg: error processing libc6-i686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.4-1ubuntu12.3); however:
  Package libc6 is not configured yet.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairomm-1.0-1:
 libcairomm-1.0-1 depends on libc6 (>= 2.4-1); however:
  Package libc6 is not configured yet.
dpkg: error processing libcairomm-1.0-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcrypt-blowfish-perl:
 libcrypt-blowfish-perl depends on libc6 (>= 2.4-1); however:
  Package libc6 is not configured yet.
dpkg: error processing libcrypt-blowfish-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6
 libc6-i686
 libc6-dev
 libcairomm-1.0-1
 libcrypt-blowfish-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@tachikoma:/home/simonb# 



```

Any ideas?  I have no idea what exactly is segfaulting, if anyone can give me pointers on how to track this down I'd appreciate it!

---

