---
title: "apt-get error, gaim"
date: 2007-02-26
forum: General Help
---

### Post by th3gh05t on 2007-02-26
Hi,

If I hover over the small orange icon in my notification area, I receive the following error:

A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: 'Unknown Error: 'exceptions.SystemError' (E:The package gaim needs to reinstalled, but I can't find an archive for it.)'

Gaim is installed and working, (currently signed online), so I can't figure out why this error is happening. I currently have version 2.0.0beta5 installed.

I want to downgrade to version 1.5, but I am unsure of how to do so.

Can you please help me so that I can get apt-get working again and downgrade Gaim?

Thanks for your time!

th3gh05t

---

### Post by Ramses de Norre on 2007-02-26
Try
```
sudo aptitude install gaim/edgy && sudo aptitude upgrade
```
replace "edgy" with "dapper" if needed.

---

### Post by th3gh05t on 2007-02-26
Hi,

I tried the command you suggested, but I got this:

```
derek@ghost:~$ sudo aptitude install gaim/dapper && sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  gaim
The following packages have been kept back:
  app-install-data-commercial bind9-host dnsutils ekiga flashplugin-nonfree gtk2-engines-pixbuf imagemagick kdelibs-bin kdelibs-data kdelibs4c2a
  language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base libbind9-0 libc6 libc6-dev libc6-i686 libdns21 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libisc11 libisccc0 libisccfg1 liblwres9 libmagick9 libpq4 libsmbclient linux-386 linux-image-386
  linux-restricted-modules-386 linux-restricted-modules-common lvm2 opera samba samba-common slocate smbclient synaptic
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 40 not upgraded.
Need to get 836kB of archives. After unpacking 2494kB will be freed.
The following packages have unmet dependencies:
  gaim: Depends: gaim-data (= 1:1.5.0+1.5.1cvs20051015-1ubuntu10) but 1:2.0.0+beta5-0ubuntu3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
gaim-data [1:2.0.0+beta5-0ubuntu3 (now) -> 1:1.5.0+1.5.1cvs20051015-1ubuntu10 (dapper)]

Score is -40

Accept this solution? [Y/n/q/?] Y
The following packages will be DOWNGRADED:
  gaim gaim-data
The following packages have been kept back:
  app-install-data-commercial bind9-host dnsutils ekiga flashplugin-nonfree gtk2-engines-pixbuf imagemagick kdelibs-bin kdelibs-data kdelibs4c2a
  language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base libbind9-0 libc6 libc6-dev libc6-i686 libdns21 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libisc11 libisccc0 libisccfg1 liblwres9 libmagick9 libpq4 libsmbclient linux-386 linux-image-386
  linux-restricted-modules-386 linux-restricted-modules-common lvm2 opera samba samba-common slocate smbclient synaptic
0 packages upgraded, 0 newly installed, 2 downgraded, 0 to remove and 40 not upgraded.
Need to get 1450kB of archives. After unpacking 7475kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com dapper/main gaim 1:1.5.0+1.5.1cvs20051015-1ubuntu10 [836kB]
Err http://archive.ubuntu.com dapper/main gaim 1:1.5.0+1.5.1cvs20051015-1ubuntu10
  Connection timed out [IP: 91.189.89.8 80]
Get:2 http://archive.ubuntu.com dapper/main gaim-data 1:1.5.0+1.5.1cvs20051015-1ubuntu10 [613kB]
Err http://archive.ubuntu.com dapper/main gaim-data 1:1.5.0+1.5.1cvs20051015-1ubuntu10
  Connection timed out [IP: 91.189.89.8 80]
E: Unable to correct for unavailable packages

```

---

### Post by Ramses de Norre on 2007-02-26
Seems like there's a problem with the server, I can't connect to it neither.
Hopefully he'll come back up soon so try again every now and then.

---

