---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-12-11
forum: General Help
---

### Post by checoimg on 2012-12-11
Hi and thank you for your time I'm trying to install GCDEmu on Quantal Quetzal andI get this error.

ubuntu@ubuntu: sudo apt-get install gcdemu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  build-essential cdemu-client cdemu-daemon dkms dpkg-dev fakeroot g++ g++-4.7
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libao-common libao4
  libmirage6 libstdc++6-4.7-dev vhba-dkms
Suggested packages:
  debhelper debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc libstdc++6-4.7-dbg
  libesd0 libesd-alsa0 libroar1 libsndio0 roaraudio-server libstdc++6-4.7-doc
The following NEW packages will be installed:
  build-essential cdemu-client cdemu-daemon dkms dpkg-dev fakeroot g++ g++-4.7 gcdemu
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libao-common libao4
  libmirage6 libstdc++6-4.7-dev vhba-dkms
0 upgraded, 17 newly installed, 0 to remove and 176 not upgraded.
Need to get 10.9 MB of archives.
After this operation, 31.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net/cdemu/ppa/ubuntu/](http://ppa.launchpad.net/cdemu/ppa/ubuntu/) quantal/main vhba-dkms all 20120422-1ubuntu0~quantal1~ppa1 [10.3 kB]
Get:2 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main libao-common all 1.1.0-1ubuntu3 [6,674 B]
Get:3 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main libao4 amd64 1.1.0-1ubuntu3 [39.7 kB]
Get:4 [http://ppa.launchpad.net/cdemu/ppa/ubuntu/](http://ppa.launchpad.net/cdemu/ppa/ubuntu/) quantal/main libmirage6 amd64 1.5.0-1ubuntu0~quantal1~ppa1 [178 kB]
Get:5 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main libstdc++6-4.7-dev amd64 4.7.2-2ubuntu1 [1,716 kB]
Get:6 [http://ppa.launchpad.net/cdemu/ppa/ubuntu/](http://ppa.launchpad.net/cdemu/ppa/ubuntu/) quantal/main cdemu-daemon amd64 1.5.0-1ubuntu0~quantal1~ppa1 [49.2 kB]
Get:7 [http://ppa.launchpad.net/cdemu/ppa/ubuntu/](http://ppa.launchpad.net/cdemu/ppa/ubuntu/) quantal/main cdemu-client all 1.5.0-1ubuntu0~quantal1~ppa2 [27.2 kB]
Get:8 [http://ppa.launchpad.net/cdemu/ppa/ubuntu/](http://ppa.launchpad.net/cdemu/ppa/ubuntu/) quantal/main gcdemu all 1.5.0-1ubuntu0~quantal1~ppa3 [35.8 kB]
Get:9 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main g++-4.7 amd64 4.7.2-2ubuntu1 [7,966 kB]
Get:10 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main g++ amd64 4:4.7.2-1ubuntu2 [1,448 B]  
Get:11 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main dpkg-dev all 1.16.7ubuntu6 [595 kB]   
Get:12 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main build-essential amd64 11.5ubuntu3 [5,814 B]
Get:13 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main dkms all 2.2.0.3-1.1ubuntu1 [72.8 kB] 
Get:14 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main fakeroot amd64 1.18.4-2 [88.2 kB]     
Get:15 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:16 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main libalgorithm-diff-xs-perl amd64 0.04-2build3 [12.5 kB]
Get:17 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) quantal/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Fetched 10.9 MB in 47s (227 kB/s)                                                              
Selecting previously unselected package libao-common.
(Reading database ... 153101 files and directories currently installed.)
Unpacking libao-common (from .../libao-common_1.1.0-1ubuntu3_all.deb) ...
Selecting previously unselected package libao4:amd64.
Unpacking libao4:amd64 (from .../libao4_1.1.0-1ubuntu3_amd64.deb) ...
Selecting previously unselected package libstdc++6-4.7-dev.
Unpacking libstdc++6-4.7-dev (from .../libstdc++6-4.7-dev_4.7.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.7.
Unpacking g++-4.7 (from .../g++-4.7_4.7.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.7.2-1ubuntu2_amd64.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.7ubuntu6_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu3_amd64.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1_all.deb) ...
Selecting previously unselected package vhba-dkms.
Unpacking vhba-dkms (from .../vhba-dkms_20120422-1ubuntu0~quantal1~ppa1_all.deb) ...
Selecting previously unselected package libmirage6.
Unpacking libmirage6 (from .../libmirage6_1.5.0-1ubuntu0~quantal1~ppa1_amd64.deb) ...
Selecting previously unselected package cdemu-daemon.
Unpacking cdemu-daemon (from .../cdemu-daemon_1.5.0-1ubuntu0~quantal1~ppa1_amd64.deb) ...
Selecting previously unselected package cdemu-client.
Unpacking cdemu-client (from .../cdemu-client_1.5.0-1ubuntu0~quantal1~ppa2_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2_amd64.deb) ...
Selecting previously unselected package gcdemu.
Unpacking gcdemu (from .../gcdemu_1.5.0-1ubuntu0~quantal1~ppa3_all.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for hicolor-icon-theme ...
Setting up libao-common (1.1.0-1ubuntu3) ...
Setting up libao4:amd64 (1.1.0-1ubuntu3) ...
Setting up dpkg-dev (1.16.7ubuntu6) ...
Setting up dkms (2.2.0.3-1.1ubuntu1) ...
Setting up libmirage6 (1.5.0-1ubuntu0~quantal1~ppa1) ...
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build3) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libstdc++6-4.7-dev (4.7.2-2ubuntu1) ...
Setting up g++-4.7 (4.7.2-2ubuntu1) ...
Setting up g++ (4:4.7.2-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up build-essential (11.5ubuntu3) ...
Setting up vhba-dkms (20120422-1ubuntu0~quantal1~ppa1) ...
Loading new vhba-20120422 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
WARNING: Group 'cdrom' already exists.
FATAL: Module vhba not found.
ERROR: Unable to load module.
dpkg: error processing vhba-dkms (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cdemu-daemon:
 cdemu-daemon depends on vhba-dkms (>= 20110915); however:
  Package vhba-dkms is not configured yet.

dpkg: error processing cdemu-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdemu-client:
 cdemu-client depends on cdemu-daemon (>= 1.5.0); however:
  Package cdemu-daemon is not configured yet.

dpkg: error processing cdemu-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcdemu:
 gcdemu depends on cdemu-daemon (>= 1.5.0); however:
  Package cdemu-daemon is not configured yet.

dpkg: error processing gcdemu (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
No apport report written because the error message indicates its a followup error from a previous failure.
          No apport report written because the error message indicates its a followup error from a previous failure.
                    No apport report written because MaxReports is reached already
                                                                                  Errors were encountered while processing:
 vhba-dkms
 cdemu-daemon
 cdemu-client
 gcdemu
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by checoimg on 2012-12-11
I tried to install it with synaptic and got this error.

E: vhba-dkms: subprocess installed post-installation script returned error exit status 1
E: cdemu-daemon: dependency problems - leaving unconfigured
E: cdemu-client: dependency problems - leaving unconfigured
E: gcdemu: dependency problems - leaving unconfigured

---

