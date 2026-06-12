---
title: "Upgrade failed....unconfigured packages"
date: 2013-10-27
forum: General Help
---

### Post by whatthefunk on 2013-10-27
I just attempted the upgrade from Kubuntu 13.04 to 13.10.  My system didnt detect that an upgrade was possible so I manually changed the repos from raring to saucy in /etc/apt and then ran sudo apt-get update & sudo apt-get dist-upgrade.  After downloading all the necessary packages, dpkg failed.

sudo dpkg --audit
```
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libpython2.7:amd64   Shared Python runtime library (version 2.7)
 libexpat1-dev:amd64  XML parsing C library - development kit
 libc6-dev:amd64      Embedded GNU C Library: Development Libraries and Header 
 libpango1.0-dev      Development files for the Pango
 plymouth             graphical boot animation and logger - main package
 libglib2.0-bin       Programs for the GLib library
 zlib1g-dev:amd64     compression library - development
 libglib2.0-dev       Development files for the GLib library

```

sudo dpkg --configure -a
```
dpkg: dependency problems prevent configuration of libpython2.7:amd64:
 libpython2.7:amd64 depends on libpython2.7-stdlib (= 2.7.5-8ubuntu3); however:
  Version of libpython2.7-stdlib:amd64 on system is 2.7.4-2ubuntu3.2.

dpkg: error processing libpython2.7:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:amd64:
 libc6-dev:amd64 depends on libc6 (= 2.17-93ubuntu4); however:
  Version of libc6:amd64 on system is 2.17-0ubuntu5.1.

dpkg: error processing libc6-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-dev:
 libpango1.0-dev depends on gir1.2-pango-1.0 (= 1.32.5-5ubuntu1); however:
  Version of gir1.2-pango-1.0 on system is 1.32.5-0ubuntu1.

dpkg: error processing libpango1.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.38.0-1ubuntu1); however:
  Version of libglib2.0-0:amd64 on system is 2.36.0-1ubuntu2.

dpkg: error processing libglib2.0-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zlib1g-dev:amd64:
 zlib1g-dev:amd64 depends on libc6-dev | libc-dev; however:
  Package libc6-dev:amd64 is not configured yet.
  Package libc-dev is not installed.
  Package libc6-dev:amd64 which provides libc-dev is not configured yet.

dpkg: error processing zlib1g-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglib2.0-dev:
 libglib2.0-dev depends on libglib2.0-0 (= 2.38.0-1ubuntu1); however:
  Version of libglib2.0-0:amd64 on system is 2.36.0-1ubuntu2.
 libglib2.0-dev depends on libglib2.0-bin (= 2.38.0-1ubuntu1); however:
  Package libglib2.0-bin is not configured yet.
 libglib2.0-dev depends on zlib1g-dev; however:
  Package zlib1g-dev:amd64 is not configured yet.

dpkg: error processing libglib2.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexpat1-dev:amd64:
 libexpat1-dev:amd64 depends on libc6-dev | libc-dev; however:
  Package libc6-dev:amd64 is not configured yet.
  Package libc-dev is not installed.
  Package libc6-dev:amd64 which provides libc-dev is not configured yet.

dpkg: error processing libexpat1-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libpython2.7:amd64
 libc6-dev:amd64
 libpango1.0-dev
 libglib2.0-bin
 zlib1g-dev:amd64
 libglib2.0-dev
 libexpat1-dev:amd64

```

sudo apt-get dist-upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.17-93ubuntu4) but 2.17-0ubuntu5.1 is installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.38.0-1ubuntu1) but 2.36.0-1ubuntu2 is installed
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.38.0-1ubuntu1) but 2.36.0-1ubuntu2 is installed
 libpango1.0-dev : Depends: gir1.2-pango-1.0 (= 1.32.5-5ubuntu1) but 1.32.5-0ubuntu1 is installed
 libpython2.7 : Depends: libpython2.7-stdlib (= 2.7.5-8ubuntu3) but 2.7.4-2ubuntu3.2 is installed
 plymouth : Depends: libplymouth2 (= 0.8.8-0ubuntu8) but 0.8.8-0ubuntu6.2 is installed
 plymouth-label : Depends: plymouth (= 0.8.8-0ubuntu6.2) but 0.8.8-0ubuntu8 is installed
E: Unmet dependencies. Try using -f.

```

My guess is that these packages are looking for the old repos, but they have been changed.  How can I correct this?  Is it safe for me to change the repos back to raring, upgrade these packages, change them to saucy and then try to continue the upgrade?

---

