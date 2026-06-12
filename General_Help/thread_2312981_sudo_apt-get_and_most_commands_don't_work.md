---
title: "sudo apt-get and most commands don't work"
date: 2016-02-08
forum: General Help
---

### Post by Seyed_Ali_Mousavi on 2016-02-08
I'm fairly new to ubuntu and i tried to uninstall and then reinstall python 3 using sudo apt-get...apparently things didnt go right and after that almost nothing works. I have no idea what to do. I am on Ubuntu 14

```

sudo apt-get install python3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpeas-1.0-0 : Depends: libpython3.4 (>= 3.4~b1) but it is not going to be installed
 python3 : Depends: python3.4 (>= 3.4.0-0~) but it is not going to be installed
           Depends: python3-minimal (= 3.4.0-0ubuntu2) but it is not going to be installed
           Depends: libpython3-stdlib (= 3.4.0-0ubuntu2) but it is not going to be installed
 python3-dev : Depends: libpython3-dev (= 3.4.0-0ubuntu2) but it is not going to be installed
               Depends: python3.4-dev (>= 3.4.0-0~) but it is not going to be installed
 rhythmbox-mozilla : Depends: rhythmbox (= 3.0.2-0ubuntu2) but it is not going to be installed
 rhythmbox-plugin-cdrecorder : Depends: rhythmbox (= 3.0.2-0ubuntu2) but it is not going to be installed
 rhythmbox-plugin-magnatune : Depends: rhythmbox (= 3.0.2-0ubuntu2) but it is not going to be installed
 sessioninstaller : Depends: aptdaemon (>= 0.30) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  apg app-install-data apport-symptoms apt-xapian-index cups-pk-helper
  duplicity gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-udisks-2.0
  gkbd-capplet gnome-control-center-shared-data intel-gpu-tools laptop-detect
  libapparmor-perl libc6-dbg libcrypt-passwdmd5-perl libgnome-control-center1
  libgnomekbd-common libgnomekbd8 librsync1 libtimezonemap1 python-debtagshw
  python-lockfile python-lxml python-oneconf python-pycurl python-xapian
  qtdeclarative5-localstorage-plugin run-one screen signon-keyring-extension
  syslinux syslinux-common syslinux-legacy tmux ubuntu-extras-keyring
  ubuntu-system-service
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dh-python python3-apt rhythmbox rhythmbox-plugin-zeitgeist rhythmbox-plugins
Suggested packages:
  python3-apt-dbg python-apt-doc gstreamer1.0-plugins-bad
  gstreamer1.0-plugins-ugly gnome-codec-install gnome-control-center
The following NEW packages will be installed:
  dh-python python3-apt rhythmbox rhythmbox-plugin-zeitgeist rhythmbox-plugins
0 upgraded, 5 newly installed, 0 to remove and 264 not upgraded.
1 not fully installed or removed.
Need to get 190 kB/580 kB of archives.
After this operation, 3,851 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dh-python all 1.20140128-1ubuntu8.2 [51.1 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-apt amd64 0.9.3.5ubuntu2 [139 kB]
Fetched 190 kB in 0s (1,144 kB/s)    
Selecting previously unselected package dh-python.
dpkg: warning: files list file for package 'screen-resolution-extra' missing; assuming package has no files currently installed
(Reading database ... 354932 files and directories currently installed.)
Preparing to unpack .../dh-python_1.20140128-1ubuntu8.2_all.deb ...
Unpacking dh-python (1.20140128-1ubuntu8.2) ...
Selecting previously unselected package python3-apt.
Preparing to unpack .../python3-apt_0.9.3.5ubuntu2_amd64.deb ...
Unpacking python3-apt (0.9.3.5ubuntu2) ...
Selecting previously unselected package rhythmbox.
Preparing to unpack .../rhythmbox_3.0.2-0ubuntu2_amd64.deb ...
Unpacking rhythmbox (3.0.2-0ubuntu2) ...
Selecting previously unselected package rhythmbox-plugin-zeitgeist.
Preparing to unpack .../rhythmbox-plugin-zeitgeist_3.0.2-0ubuntu2_all.deb ...
Unpacking rhythmbox-plugin-zeitgeist (3.0.2-0ubuntu2) ...
Selecting previously unselected package rhythmbox-plugins.
Preparing to unpack .../rhythmbox-plugins_3.0.2-0ubuntu2_amd64.deb ...
Unpacking rhythmbox-plugins (3.0.2-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
dpkg: error processing package python3 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 rhythmbox depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-zeitgeist:
 rhythmbox-plugin-zeitgeist depends on rhythmbox (>= 3.0); however:
  Package rhythmbox is not configured yet.
 rhythmbox-plugin-zeitgeist depends on rhythmbox (<< 3.1); however:
  Package rhythmbox is not configured yet.

dpkg: error processing package rhythmbox-plugin-zeitgeist (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugins:
 rhythmbox-plugins depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 rhythmbox-plugins depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 rhythmbox-plugins depends on rhythmbox (= 3.0.2-0ubuntu2); however:
  Package rhythmbox is not configured yet.

dpkg: error processing package rhythmbox-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dh-python:
 dh-python depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package dh-python (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3
 python3-apt
 rhythmbox
 rhythmbox-plugin-zeitgeist
 rhythmbox-plugins
 dh-python
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



```

sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugins:
 rhythmbox-plugins depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 rhythmbox-plugins depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package rhythmbox-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 rhythmbox depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-oneconf:
 python3-oneconf depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-oneconf depends on python3-apt; however:
  Package python3-apt is not configured yet.


dpkg: error processing package python3-oneconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.4); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of oneconf:
 oneconf depends on python3-oneconf; however:
  Package python3-oneconf is not configured yet.


dpkg: error processing package oneconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dh-python:
 dh-python depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package dh-python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 onboard depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package onboard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-zeitgeist:
 rhythmbox-plugin-zeitgeist depends on rhythmbox (>= 3.0); however:
  Package rhythmbox is not configured yet.
 rhythmbox-plugin-zeitgeist depends on rhythmbox (<< 3.1); however:
  Package rhythmbox is not configured yet.


dpkg: error processing package rhythmbox-plugin-zeitgeist (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard-data:
 onboard-data depends on onboard (>= 0.99.0~alpha1~tr1507); however:
  Package onboard is not configured yet.


dpkg: error processing package onboard-data (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3-apt
 rhythmbox-plugins
 rhythmbox
 python3-oneconf
 python3-gdbm:amd64
 oneconf
 dh-python
 onboard
 rhythmbox-plugin-zeitgeist
 onboard-data

```




```

sudo apt-get -u dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apg app-install-data apport-symptoms apt-xapian-index cups-pk-helper
  duplicity gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-udisks-2.0
  gkbd-capplet gnome-control-center-shared-data intel-gpu-tools laptop-detect
  libapparmor-perl libc6-dbg libcrypt-passwdmd5-perl libgnome-control-center1
  libgnomekbd-common libgnomekbd8 librsync1 libtimezonemap1
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-signed-image-3.16.0-30-generic python-debtagshw python-lockfile
  python-lxml python-oneconf python-pycurl python-xapian
  qtdeclarative5-localstorage-plugin signon-keyring-extension syslinux
  syslinux-common syslinux-legacy ubuntu-extras-keyring ubuntu-system-service
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0 B/8,666 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package python3 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.4); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 onboard depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package onboard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard-data:
 onboard-data depends on onboard (>= 0.99.0~alpha1~tr1507); however:
  Package onboard is not configured yet.


dpkg: error processing package onboard-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 rhythmbox depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugins:
 rhythmbox-plugins depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 rhythmbox-plugins depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 rhythmbox-plugins depends on rhythmbox (= 3.0.2-0ubuntu2); however:
  Package rhythmbox is not configured yet.


dpkg: error processing package rhythmbox-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-zeitgeist:
 rhythmbox-plugin-zeitgeist depends on rhythmbox (>= 3.0); however:
  Package rhythmbox is not configured yet.
 rhythmbox-plugin-zeitgeist depends on rhythmbox (<< 3.1); however:
  Package rhythmbox is not configured yet.


dpkg: error processing package rhythmbox-plugin-zeitgeist (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-oneconf:
 python3-oneconf depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-oneconf depends on python3-apt; however:
  Package python3-apt is not configured yet.


dpkg: error processing package python3-oneconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of oneconf:
 oneconf depends on python3-oneconf; however:
  Package python3-oneconf is not configured yet.


dpkg: error processing package oneconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dh-python:
 dh-python depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package dh-python (--configure):
 dependency problems - leaving unconfigured
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

sudo apt-get install python3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3 is already the newest version.
The following packages were automatically installed and are no longer required:
  apg app-install-data apport-symptoms apt-xapian-index cups-pk-helper
  duplicity gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-udisks-2.0
  gkbd-capplet gnome-control-center-shared-data intel-gpu-tools laptop-detect
  libapparmor-perl libc6-dbg libcrypt-passwdmd5-perl libgnome-control-center1
  libgnomekbd-common libgnomekbd8 librsync1 libtimezonemap1
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-signed-image-3.16.0-30-generic python-debtagshw python-lockfile
  python-lxml python-oneconf python-pycurl python-xapian
  qtdeclarative5-localstorage-plugin signon-keyring-extension syslinux
  syslinux-common syslinux-legacy ubuntu-extras-keyring ubuntu-system-service
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0 B/8,666 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package python3 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.4); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 onboard depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package onboard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard-data:
 onboard-data depends on onboard (>= 0.99.0~alpha1~tr1507); however:
  Package onboard is not configured yet.


dpkg: error processing package onboard-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 rhythmbox depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugins:
 rhythmbox-plugins depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 rhythmbox-plugins depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 rhythmbox-plugins depends on rhythmbox (= 3.0.2-0ubuntu2); however:
  Package rhythmbox is not configured yet.


dpkg: error processing package rhythmbox-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-zeitgeist:
 rhythmbox-plugin-zeitgeist depends on rhythmbox (>= 3.0); however:
  Package rhythmbox is not configured yet.
 rhythmbox-plugin-zeitgeist depends on rhythmbox (<< 3.1); however:
  Package rhythmbox is not configured yet.


dpkg: error processing package rhythmbox-plugin-zeitgeist (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-oneconf:
 python3-oneconf depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-oneconf depends on python3-apt; however:
  Package python3-apt is not configured yet.


dpkg: error processing package python3-oneconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of oneconf:
 oneconf depends on python3-oneconf; however:
  Package python3-oneconf is not configured yet.


dpkg: error processing package oneconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dh-python:
 dh-python depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package dh-python (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3
 python3-apt
 python3-gdbm:amd64
 onboard
 onboard-data
 rhythmbox
 rhythmbox-plugins
 rhythmbox-plugin-zeitgeist
 python3-oneconf
 oneconf
 dh-python
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

```

cat /etc/apt/sources.list.d/*
deb http://ppa.launchpad.net/x2go/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/x2go/stable/ubuntu trusty main

```


```

 apt-get download libssl1.0.0 libpython3.4-minimal; sudo dpkg -i libssl1.0.0*.deb libpython3.4-minimal*.deb
dpkg: warning: files list file for package 'screen-resolution-extra' missing; assuming package has no files currently installed
(Reading database ... 384580 files and directories currently installed.)
Preparing to unpack libssl1.0.0_1.0.1f-1ubuntu2.16_amd64.deb ...
Unpacking libssl1.0.0:amd64 (1.0.1f-1ubuntu2.16) over (1.0.1f-1ubuntu2.16) ...
Preparing to unpack libpython3.4-minimal_3.4.3-1ubuntu1~14.04.3_amd64.deb ...
Unpacking libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.3) over (3.4.3-1ubuntu1~14.04.3) ...
Setting up libssl1.0.0:amd64 (1.0.1f-1ubuntu2.16) ...
Setting up libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.3) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
/sbin/ldconfig.real: /usr/local/cuda-7.0/lib64/libcudnn.so.7.0 is not a symbolic link

```

note that "/usr/local/cuda-7.0/lib64/" has been added to LD_LIBRARY_PATH



on top of that wget and nvidia-smi doesnt work


I am clueless what to do.....have no idea what to do??
If I install python3 from source will it solve it?

---

### Post by matt_symes on 2016-02-08
Hi

You tried to uninstall python3 ?

It may be quicker for you to backup and reinstall.

Is that possible ?

Kind regards

---

### Post by Seyed_Ali_Mousavi on 2016-02-09
yes i did try uninstall as well i  here is what i got

```

sudo apt-get remove python3
[sudo] password for ali: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  account-plugin-twitter apg app-install-data appmenu-qt appmenu-qt5
  apport-symptoms apt-xapian-index avahi-utils bamfdaemon
  command-not-found-data cups-pk-helper dc dmidecode dnsmasq-base duplicity
  gedit-common gir1.2-accounts-1.0 gir1.2-appindicator3-0.1 gir1.2-atspi-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-gdata-0.0
  gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomekeyring-1.0
  gir1.2-goa-1.0 gir1.2-gtksource-3.0 gir1.2-gudev-1.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-messagingmenu-1.0
  gir1.2-networkmanager-1.0 gir1.2-notify-0.7 gir1.2-secret-1
  gir1.2-signon-1.0 gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-webkit-3.0
  gir1.2-wnck-3.0 gkbd-capplet gnome-calculator
  gnome-control-center-shared-data indicator-appmenu indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-printers
  indicator-session indicator-sound intel-gpu-tools iputils-arping
  laptop-detect libapparmor-perl libbamf3-2 libc6-dbg libcrypt-passwdmd5-perl
  libdmapsharing-3.0-2 libgail-common libgail18 libgee2 libglew1.10
  libglewmx1.10 libgnome-bluetooth11 libgnome-control-center1
  libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0
  libgnomekbd-common libgnomekbd8 libgpod-common libgpod4
  libgtksourceview-3.0-1 libgtksourceview-3.0-common liblightdm-gobject-1-0
  liblouis-data liblouis2 libmnl0 libnetfilter-conntrack3 libnl-route-3-200
  libnm-glib-vpn1 libnm-gtk-common libnm-gtk0 libnux-4.0-0 libnux-4.0-common
  librsync1 libsgutils2-2 libtimezonemap1 libunity-core-6.0-9
  libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-misc4
  liburl-dispatcher1 lightdm linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic linux-signed-image-3.16.0-30-generic
  media-player-info mobile-broadband-provider-info mousetweaks mscompress
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome nux-tools obexd-client oneconf-common
  plainbox-secure-policy pptp-linux python-cups python-cupshelpers
  python-debtagshw python-gdbm python-gnomekeyring python-libxml2
  python-lockfile python-lxml python-newt python-oneconf
  python-piston-mini-client python-pycurl python-smbc python-xapian
  qtdeclarative5-localstorage-plugin rhythmbox-data run-one screen
  signon-keyring-extension syslinux syslinux-common syslinux-legacy
  system-config-printer-common system-config-printer-udev telepathy-indicator
  tmux ubuntu-extras-keyring ubuntu-system-service unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-music unity-lens-video
  unity-scope-musicstores unity-scope-video-remote unity-scopes-master-default
  unity-scopes-runner unity-services wpasupplicant
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-newt
The following packages will be REMOVED:
  byobu dh-python firefox foomatic-db-compressed-ppds friends
  friends-dispatcher friends-facebook friends-twitter gedit gnome-menus
  gnome-orca gnome-sudoku language-selector-common libfriends0 lsb lsb-core
  lsb-cxx lsb-desktop lsb-graphics lsb-languages lsb-multimedia lsb-printing
  lsb-release onboard onboard-data oneconf openprinting-gutenprint
  openprinting-ppds plainbox-provider-checkbox
  plainbox-provider-resource-generic printer-driver-foo2zjs
  printer-driver-foo2zjs-common printer-driver-postscript-hp
  printer-driver-ptouch printer-driver-pxljr python-commandnotfound python3
  python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet
  python3-checkbox-support python3-commandnotfound python3-crypto python3-dbus
  python3-debian python3-defer python3-feedparser python3-gdbm python3-gi
  python3-gi-cairo python3-httplib2 python3-louis python3-lxml python3-mako
  python3-markupsafe python3-newt python3-oauthlib python3-oneconf
  python3-piston-mini-client python3-pkg-resources python3-plainbox
  python3-pyatspi python3-pycurl python3-pyparsing python3-six python3-speechd
  python3-xdg python3-xkit rhythmbox rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins screen-resolution-extra
  software-center-aptdaemon-plugins system-config-printer-gnome ubuntu-minimal
  ubuntu-standard ufw unity unity-lens-friends unity-lens-photos
  unity-scope-audacious unity-scope-calculator unity-scope-chromiumbookmarks
  unity-scope-clementine unity-scope-colourlovers unity-scope-devhelp
  unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-gmusicbrowser
  unity-scope-gourmet unity-scope-guayadeque unity-scope-home
  unity-scope-manpages unity-scope-musique unity-scope-openclipart
  unity-scope-texdoc unity-scope-tomboy unity-scope-virtualbox
  unity-scope-yelp unity-scope-zotero update-notifier-common
The following NEW packages will be installed:
  python-newt
0 upgraded, 1 newly installed, 108 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 18.3 kB of archives.
After this operation, 245 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main python-newt amd64 0.52.15-2ubuntu5 [18.3 kB]
Fetched 18.3 kB in 0s (379 kB/s)       
dpkg: warning: files list file for package 'screen-resolution-extra' missing; assuming package has no files currently installed
(Reading database ... 384579 files and directories currently installed.)
Removing rhythmbox-plugins (3.0.2-0ubuntu2) ...
Removing update-notifier-common (0.154.1ubuntu1) ...
Removing rhythmbox-plugin-zeitgeist (3.0.2-0ubuntu2) ...
Removing python3-debian (0.1.21+nmu2ubuntu2) ...
Removing python3-six (1.5.2-1ubuntu1) ...
Removing dh-python (1.20140128-1ubuntu8.2) ...
Removing onboard-data (1.0.1-0ubuntu1) ...
Removing onboard (1.0.1-0ubuntu1) ...
Removing oneconf (0.3.7.14.04.1) ...
Removing python3-oneconf (0.3.7.14.04.1) ...
Removing system-config-printer-gnome (1.4.3+20140219-0ubuntu2.6) ...
Removing python3-aptdaemon.pkcompat (1.1.1-1ubuntu5.2) ...
Removing python3-commandnotfound (0.3ubuntu12) ...
Removing python3-gdbm:amd64 (3.4.3-1~14.04.2) ...
Removing byobu (5.77-0ubuntu1.2) ...
Removing firefox (44.0.1+build2-0ubuntu0.14.04.1) ...
Removing foomatic-db-compressed-ppds (20140410-0ubuntu1) ...
Removing unity-lens-friends (0.1.3+14.04.20140317-0ubuntu1) ...
Removing friends-twitter (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing libfriends0:amd64 (0.1.2+14.04.20131108.1-0ubuntu1) ...
Removing friends-facebook (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing gedit (3.10.4-0ubuntu4) ...
Removing gnome-menus (3.10.1-0ubuntu2) ...
Removing gnome-orca (3.10.3-0ubuntu1) ...
Removing gnome-sudoku (1:3.10.2-0ubuntu3.1) ...
Removing ubuntu-standard (1.325) ...
Removing language-selector-common (0.129.3) ...
Removing openprinting-gutenprint (5.2.7-1lsb3.2) ...
cups stop/waiting
cups start/running, process 16632
Removing lsb (4.1+Debian11ubuntu6) ...
Removing lsb-printing (4.1+Debian11ubuntu6) ...
Removing lsb-desktop (4.1+Debian11ubuntu6) ...
Removing lsb-multimedia (4.1+Debian11ubuntu6) ...
Removing lsb-cxx (4.1+Debian11ubuntu6) ...
Removing lsb-graphics (4.1+Debian11ubuntu6) ...
Removing lsb-languages (4.1+Debian11ubuntu6) ...
Removing unity (7.2.6+14.04.20151021-0ubuntu1) ...
Removing unity-scope-home (6.8.2+14.04.20131029.1-0ubuntu1) ...
Removing ubuntu-minimal (1.325) ...
Removing openprinting-ppds (20140410-0ubuntu1) ...
Removing plainbox-provider-checkbox (0.4-1) ...
Removing plainbox-provider-resource-generic (0.3-1) ...
Removing printer-driver-foo2zjs (20140209dfsg0-1ubuntu1) ...
Removing printer-driver-foo2zjs-common (20140209dfsg0-1ubuntu1) ...
Removing printer-driver-postscript-hp (3.14.3-0ubuntu3.4) ...
Removing printer-driver-ptouch (1.3-8) ...
Removing printer-driver-pxljr (1.4+repack0-3) ...
Removing python-commandnotfound (0.3ubuntu12) ...
Removing python3-aptdaemon.gtk3widgets (1.1.1-1ubuntu5.2) ...
Removing python3-brlapi (5.0-2ubuntu2) ...
Removing python3-gi-cairo (3.12.0-1ubuntu1) ...
Removing python3-cairo (1.10.0+dfsg-3ubuntu2) ...
Removing python3-chardet (2.2.1-2~ubuntu1) ...
Removing python3-checkbox-support (0.2-1) ...
Removing unity-lens-photos (1.0+14.04.20140318-0ubuntu1) ...
Removing python3-piston-mini-client (0.7.5-0ubuntu2) ...
Removing unity-scope-musique (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-guayadeque (0.1+13.10.20130927.1-0ubuntu1) ...
Removing unity-scope-openclipart (0.1+13.10.20130723-0ubuntu1) ...
Removing python3-feedparser (5.1.3-2) ...
Removing unity-scope-zotero (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-yelp (0.1+13.10.20130723-0ubuntu1) ...
Removing python3-httplib2 (0.8-2build1) ...
Removing python3-louis (2.5.3-2ubuntu1) ...
Removing unity-scope-devhelp (0.1+14.04.20140328-0ubuntu1) ...
Removing python3-plainbox (0.5.3-2) ...
Removing python3-lxml (3.3.3-1ubuntu0.1) ...
Removing python3-mako (0.9.1-1) ...
Removing python3-markupsafe (0.18-1build2) ...
Removing python3-newt (0.52.15-2ubuntu5) ...
Removing python3-pyatspi (2.10.0+dfsg-1) ...
Removing python3-pycurl (7.19.3-0ubuntu3) ...
Removing python3-pyparsing (2.0.1+dfsg1-1build1) ...
Removing python3-speechd (0.8-5ubuntu1) ...
Removing python3-xdg (0.25-4) ...
Removing screen-resolution-extra (0.17.1) ...
Removing python3-xkit (0.5.0ubuntu2) ...
Removing rhythmbox-mozilla (3.0.2-0ubuntu2) ...
Removing rhythmbox-plugin-cdrecorder (3.0.2-0ubuntu2) ...
Removing rhythmbox-plugin-magnatune (3.0.2-0ubuntu2) ...
Removing software-center-aptdaemon-plugins (0.1.6build1) ...
Removing ufw (0.34~rc-0ubuntu2) ...
Skip stopping firewall: ufw (not enabled)
Removing unity-scope-audacious (0.1+13.10.20130927.1-0ubuntu1) ...
Removing unity-scope-calculator (0.1+14.04.20140328-0ubuntu1) ...
Removing unity-scope-chromiumbookmarks (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-clementine (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-colourlovers (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-firefoxbookmarks (0.1+13.10.20130809.1-0ubuntu1) ...
Removing unity-scope-gdrive (0.9+13.10.20130723-0ubuntu1) ...
Removing unity-scope-gmusicbrowser (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-gourmet (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-manpages (3.0+14.04.20140324-0ubuntu1) ...
Removing unity-scope-texdoc (0.1+14.04.20140328-0ubuntu1) ...
Removing unity-scope-tomboy (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-virtualbox (0.1+13.10.20130723-0ubuntu1) ...
Removing rhythmbox (3.0.2-0ubuntu2) ...
Removing python3-aptdaemon (1.1.1-1ubuntu5.2) ...
Removing python3-apt (0.9.3.5ubuntu2) ...
Removing friends (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing friends-dispatcher (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing lsb-core (4.1+Debian11ubuntu6) ...
Removing lsb-release (4.1+Debian11ubuntu6) ...
Removing python3-oauthlib (0.6.1-1) ...
Removing python3-crypto (2.6.1-4build1) ...
Removing python3-dbus (1.2.0-2build2) ...
Removing python3-defer (1.0.6-2build1) ...
Removing python3-gi (3.12.0-1ubuntu1) ...
Removing python3-pkg-resources (3.3-1ubuntu2) ...
dpkg: error processing package python3 (--remove):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for cups (1.7.2-0ubuntu1.7) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
/sbin/ldconfig.real: /usr/local/cuda-7.0/lib64/libcudnn.so.7.0 is not a symbolic link


/sbin/ldconfig.real: /usr/local/cuda/lib64/libcudnn.so.4 is not a symbolic link


Processing triggers for doc-base (0.10.5) ...
Processing 1 removed doc-base file...
Errors were encountered while processing:
 python3
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

when you say backup and reinstall what are you referring to ubuntu?

---

### Post by matt_symes on 2016-02-09
Hi

> when you say backup and reinstall what are you referring to ubuntu? 

Yeah. It just may be quicker to do that.

Python 3 is a dependency package and so will have pulled in other packages.

> This package is a dependency package, which depends on Debian's default
 Python 3 version (currently v3.5).

A lot of packages are dependent upon it and that's why apt is showing you that list of packages that it now thinks are no longer required.

It get an idea of what depends on python3 (and that you have installed on your system), copy and paste this into the terminal

```
apt-cache --installed rdepends ^python3$ | sort
```

You could try to fix this but it may be quicker to backup and reinstall.

However, if you choose otherwise, these are python3's direct dependencies

```
media-server1:/home/matthew:5 % apt-cache depends ^python3$
python3
  Depends: python3.4
  Depends: python3-minimal
  Depends: libpython3-stdlib
  Depends: dh-python
  Suggests: python3-doc
  Suggests: python3-tk
  Replaces: python3-minimal
  Replaces: python3-minimal:i386
  Conflicts: python3:i386
media-server1:/home/matthew:5 % 
```

The other thing you could you could is look at your dpkg logs and see what packages were removed when you uninstalled python3 and reinstall them.

grep these two log files => /var/log/dpkg.log{,.1}

The thing is, I've never uninstalled python like you have so i don't know i it's a big job to fix it or not.

I'm not sure what the best advice i can give you is.

Kind regards

---

### Post by Seyed_Ali_Mousavi on 2016-02-10
Hi Matt, i solved it.

I followed your steps to download the package one by one. It was not working. Then I truied reinstall Python3. I swear i remember running it before and having issues but this time it worked. Magic. I just did:

```
[COLOR=#263238][FONT=arial]sudo apt-get install --reinstall python3
```

Thats the solution.
Thank You[/FONT][/COLOR]

---

### Post by matt_symes on 2016-02-10
Hi

> **Seyed_Ali_Mousavi said:**
> Hi Matt, i solved it.

I followed your steps to download the package one by one. It was not working. Then I truied reinstall Python3. I swear i remember running it before and having issues but this time it worked. Magic. I just did:

```
sudo apt-get install --reinstall python3
```

Thats the solution.
Thank You

Excellent. I'm glad it's fixed :)

When you downloaded the package did you install them using *dpkg -i *.deb* ? 

If so, did any of them install ? 

If they did install this may have helped apt to reinstall the python package. 

You did something to help apt out if you had tried reinstalling python3 before.

Could you please mark this thread as SOLVED using the thread tools menu above post #1.
 
Kind regards

---

