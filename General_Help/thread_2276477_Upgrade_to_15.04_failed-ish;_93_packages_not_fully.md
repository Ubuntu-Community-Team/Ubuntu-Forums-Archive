---
title: "Upgrade to 15.04 failed-ish; 93 packages not fully installed"
date: 2015-05-02
forum: General Help
---

### Post by xmbwd on 2015-05-02
I was running 14.10 smoothly.  I tried the upgrade to 15.04.  During the install, I received the following error:

[IMG]https://dl.dropboxusercontent.com/u/13392425/Screenshot%20from%202015-05-02%2014%3A28%3A17.png[/IMG]

After the 15.04 finished installing, I got another error message that the install encountered errors.  Now, I have 93 packages "not fully installed or removed."   It actually seems to be running fine, but when I try:

```
sudo apt-get upgrade
``` *or*
```
sudo apt-get autoclean
``` *or*
```
sudo apt-get autoremove
```

I get this (long) error message, that seems to involve, among others, python3:

```
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up python3 (3.4.3-1) ...
running python rtupdate hooks for python3.4...
dpkg-query: package 'rhythmbox-plugin-magnatune' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-magnatune
error running python rtupdate hook rhythmbox-plugin-magnatune
dpkg: error processing package python3 (--configure):
 subprocess installed post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python3; however:
  Package python3 is not configured yet.
 language-selector-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 language-selector-common depends on python3-apt (>= 0.7.12.0); however:
  Package python3-apt is not configured yet.

dpkg: error processing package language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3; however:
  Package python3 is not configured yet.
 ubuntu-drivers-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 ubuntu-drivers-common depends on python3-apt; however:
  Package python3-apt is not configured yet.

dpkg: error processing package ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python3:any; however:
  Package python3 is not configured yet.
 update-notifier-common depends on python3-apt; however:
  Package python3-apt is not configured yet.

dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.4); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-commandnotfound:
 python3-commandnotfound depends on python3-apt; however:
  Package python3-apt is not configured yet.
 python3-commandnotfound depends on python3-gdbm; however:
  Package python3-gdbm:amd64 is not configured yet.
 python3-commandnotfound depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-commandnotfound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of command-not-found:
 command-not-found depends on python3-commandnotfound (>= 0.3ubuntu7); however:
  Package python3-commandnotfound is not configured yet.

dpkg: error processing package command-not-found (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-distupgrade depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.

dpkg: error processing package python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-update-manager depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing package python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3; however:
  Package python3 is not configured yet.
 ubuntu-release-upgrader-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:15.04.14); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing package ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ufw:
 ufw depends on python3; however:
  Package python3 is not configured yet.
 ufw depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ufw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3; however:
  Package python3 is not configured yet.
 update-manager-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 update-manager-core depends on python3-update-manager (= 1:15.04.7); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing package update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl-common:
 apturl-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 apturl-common depends on python3-apt; however:
  Package python3-apt is not configured yet.
 apturl-common depends on python3-update-manager; however:
  Package python3-update-manager is not configured yet.

dpkg: error processing package apturl-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on python3; however:
  Package python3 is not configured yet.
 unattended-upgrades depends on python3-apt; however:
  Package python3-apt is not configured yet.

dpkg: error processing package unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3; however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3-apt (>= 0.6.20ubuntu16); however:
  Package python3-apt is not configured yet.
 python3-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.

dpkg: error processing package python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3; however:
  Package python3 is not configured yet.
 software-properties-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 software-properties-common depends on python3-software-properties (= 0.96.4); however:
  Package python3-software-properties is not configured yet.

dpkg: error processing package software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3:any (>= 3.4); however:
  Package python3 is not configured yet.
 python3-pkg-resources depends on python3:any (<< 3.5); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon:
 python3-aptdaemon depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon depends on python3-apt (>= 0.8.5~ubuntu1); however:
  Package python3-apt is not configured yet.
 python3-aptdaemon depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.

dpkg: error processing package python3-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon.gtk3widgets:
 python3-aptdaemon.gtk3widgets depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon.gtk3widgets depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package python3-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3; however:
  Package python3 is not configured yet.
 software-properties-gtk depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 software-properties-gtk depends on python3-software-properties (= 0.96.4); however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not configured yet.
 software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.75); however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing package software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on python3; however:
  Package python3 is not configured yet.
 apturl depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 apturl depends on apturl-common (= 0.5.2ubuntu6); however:
  Package apturl-common is not configured yet.
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
 apturl depends on python3-aptdaemon; however:
  Package python3-aptdaemon is not configured yet.
 apturl depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.

dpkg: error processing package apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
  Package update-notifier-common is not configured yet.

dpkg: error processing package flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of foomatic-db-compressed-ppds:
 foomatic-db-compressed-ppds depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package foomatic-db-compressed-ppds (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-ibus-1.0:amd64:
 gir1.2-ibus-1.0:amd64 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package gir1.2-ibus-1.0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on python3; however:
  Package python3 is not configured yet.
 gnome-menus depends on python3:any (>= 3.1~); however:
  Package python3 is not configured yet.

dpkg: error processing package gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-brlapi:
 python3-brlapi depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-brlapi depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-brlapi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-cairo:
 python3-cairo depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-cairo depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-cairo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pyatspi:
 python3-pyatspi depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pyatspi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-speechd:
 python3-speechd depends on python3; however:
  Package python3 is not configured yet.
 python3-speechd depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-speechd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-orca:
 gnome-orca depends on python3; however:
  Package python3 is not configured yet.
 gnome-orca depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 gnome-orca depends on python3-brlapi (>= 0.5.1); however:
  Package python3-brlapi is not configured yet.
 gnome-orca depends on python3-cairo; however:
  Package python3-cairo is not configured yet.
 gnome-orca depends on python3-pyatspi (>= 2.10); however:
  Package python3-pyatspi is not configured yet.
 gnome-orca depends on python3-speechd (>= 0.8); however:
  Package python3-speechd is not configured yet.

dpkg: error processing package gnome-orca (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon.pkcompat:
 python3-aptdaemon.pkcompat depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon.pkcompat depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package python3-aptdaemon.pkcompat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer1.0-packagekit:
 gstreamer1.0-packagekit depends on python3-aptdaemon.pkcompat | packagekit-system-interface | packagekit (= 0.8.17-4ubuntu4); however:
  Package python3-aptdaemon.pkcompat is not configured yet.
  Package packagekit-system-interface is not installed.
  Package python3-aptdaemon.pkcompat which provides packagekit-system-interface is not configured yet.
  Package packagekit is not installed.

dpkg: error processing package gstreamer1.0-packagekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip-data:
 hplip-data depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package hplip-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pil:amd64:
 python3-pil:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-pil:amd64 depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pil:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pexpect:
 python3-pexpect depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pexpect (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-reportlab-accel:amd64:
 python3-reportlab-accel:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-reportlab-accel:amd64 depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-reportlab-accel:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-reportlab:
 python3-reportlab depends on python3-reportlab-accel (>= 3.1.44-1); however:
  Package python3-reportlab-accel:amd64 is not configured yet.
 python3-reportlab depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-reportlab (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on hplip-data (= 3.15.2-0ubuntu4); however:
  Package hplip-data is not configured yet.
 hplip depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 hplip depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 hplip depends on python3-pil; however:
  Package python3-pil:amd64 is not configured yet.
 hplip depends on python3-pexpect; however:
  Package python3-pexpect is not configured yet.
 hplip depends on python3-reportlab; however:
  Package python3-reportlab is not configured yet.

dpkg: error processing package hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on python3; however:
  Package python3 is not configured yet.
 printer-driver-postscript-hp depends on hplip (>= 3.15.2-0ubuntu4); however:
  Package hplip is not configured yet.

dpkg: error processing package printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus:
 ibus depends on gir1.2-ibus-1.0 (= 1.5.9-1ubuntu3); however:
  Package gir1.2-ibus-1.0:amd64 is not configured yet.
 ibus depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ibus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus-table:
 ibus-table depends on ibus (>= 1.5.0); however:
  Package ibus is not configured yet.
 ibus-table depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ibus-table (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing package kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k4dirstat:
 k4dirstat depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package k4dirstat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python3; however:
  Package python3 is not configured yet.
 aptdaemon depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 aptdaemon depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 python3
 python3-apt
 language-selector-common
 ubuntu-drivers-common
 update-notifier-common
 ubuntu-minimal
 apparmor
 python3-gdbm:amd64
 python3-commandnotfound
 command-not-found
 python3-distupgrade
 python3-update-manager
 ubuntu-release-upgrader-core
 ubuntu-standard
 ufw
 update-manager-core
 apturl-common
 unattended-upgrades
 python3-software-properties
 software-properties-common
 python3-pkg-resources
 python3-aptdaemon
 python3-aptdaemon.gtk3widgets
 software-properties-gtk
 apturl
 flashplugin-installer
 foomatic-db-compressed-ppds
 gedit
 gir1.2-ibus-1.0:amd64
 gnome-menus
 python3-brlapi
 python3-cairo
 python3-pyatspi
 python3-speechd
 gnome-orca
 gnome-terminal
 python3-aptdaemon.pkcompat
 gstreamer1.0-packagekit
 hplip-data
 python3-pil:amd64
 python3-pexpect
 python3-reportlab-accel:amd64
 python3-reportlab
 hplip
 printer-driver-postscript-hp
 ibus
 ibus-table
 kde-runtime
 k4dirstat
 kdepim-runtime
 aptdaemon
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can't tell if my upgrade is just shot -- and for whatever reason I just can't do it.  Or if this is something that is fixable.

Any ideas??

EDIT:  I should note that this is the third time I tried upgrading.  Each time, I went back to a 14.10 backup that I had made in 14.10.

---

### Post by Frogs Hair on 2015-05-02
Post the output of the following. ```
sudo dpkg --configure -a 
```

---

### Post by xmbwd on 2015-05-02
Thanks.  Unfortunately, it gives the same long error list:

```
sudo dpkg --configure -a
Setting up python3 (3.4.3-1) ...
running python rtupdate hooks for python3.4...
dpkg-query: package 'rhythmbox-plugin-magnatune' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-magnatune
error running python rtupdate hook rhythmbox-plugin-magnatune
dpkg: error processing package python3 (--configure):
 subprocess installed post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python3:any; however:
  Package python3 is not configured yet.

dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-lxml:
 python3-lxml depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-lxml depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-lxml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of usb-creator-gtk:
 usb-creator-gtk depends on python3; however:
  Package python3 is not configured yet.
 usb-creator-gtk depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package usb-creator-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-brlapi:
 python3-brlapi depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-brlapi depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-brlapi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-mako:
 python3-mako depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-mako (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-commandnotfound:
 python3-commandnotfound depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-commandnotfound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python3; however:
  Package python3 is not configured yet.
 language-selector-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-foo2zjs-common:
 printer-driver-foo2zjs-common depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package printer-driver-foo2zjs-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on python3-lxml; however:
  Package python3-lxml is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-six:
 python3-six depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-six (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openprinting-ppds:
 openprinting-ppds depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package openprinting-ppds (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon.gtk3widgets:
 python3-aptdaemon.gtk3widgets depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on python3; however:
  Package python3 is not configured yet.
 apturl depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 apturl depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.

dpkg: error processing package apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of command-not-found:
 command-not-found depends on python3-commandnotfound (>= 0.3ubuntu7); however:
  Package python3-commandnotfound is not configured yet.

dpkg: error processing package command-not-found (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip-data:
 hplip-data depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package hplip-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3:any (>= 3.4); however:
  Package python3 is not configured yet.
 python3-pkg-resources depends on python3:any (<< 3.5); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3; however:
  Package python3 is not configured yet.
 ubuntu-release-upgrader-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-bs4:
 python3-bs4 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-bs4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-problem-report:
 python3-problem-report depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-reportlab:
 python3-reportlab depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-reportlab (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-feedparser:
 python3-feedparser depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-feedparser (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3; however:
  Package python3 is not configured yet.
 ubuntu-drivers-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 python3-uno depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus:
 ibus depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ibus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3; however:
  Package python3 is not configured yet.
 software-properties-gtk depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 software-properties-gtk depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.
 software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.75); however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing package software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl-common:
 apturl-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 apturl-common depends on python3-update-manager; however:
  Package python3-update-manager is not configured yet.

dpkg: error processing package apturl-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pexpect:
 python3-pexpect depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pexpect (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-chardet:
 python3-chardet depends on python3; however:
  Package python3 is not configured yet.
 python3-chardet depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-chardet depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.

dpkg: error processing package python3-chardet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon:
 python3-aptdaemon depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.

dpkg: error processing package python3-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xdiagnose:
 xdiagnose depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 xdiagnose depends on python3-apport; however:
  Package python3-apport is not configured yet.

dpkg: error processing package xdiagnose (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 3.160); however:
  Package update-notifier-common is not configured yet.

dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-html5lib:
 python3-html5lib depends on python3-six; however:
  Package python3-six is not configured yet.
 python3-html5lib depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-html5lib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python3; however:
  Package python3 is not configured yet.
 aptdaemon depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 aptdaemon depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on openprinting-ppds; however:
  Package openprinting-ppds is not configured yet.
 ubuntu-desktop depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
 ubuntu-desktop depends on system-config-printer-gnome; however:
  Package system-config-printer-gnome is not configured yet.
 ubuntu-desktop depends on ubuntu-drivers-common; however:
  Package ubuntu-drivers-common is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
 ubuntu-desktop depends on xdiagnose; however:
  Package xdiagnose is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-httplib2:
 python3-httplib2 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-httplib2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-requests:
 python3-requests depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-requests depends on python3-chardet; however:
  Package python3-chardet is not configured yet.

dpkg: error processing package python3-requests (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-foo2zjs:
 printer-driver-foo2zjs depends on printer-driver-foo2zjs-common (>= 20150214dfsg0-0ubuntu1); however:
  Package printer-driver-foo2zjs-common is not configured yet.

dpkg: error processing package printer-driver-foo2zjs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-cupshelpers:
 python3-cupshelpers depends on python3-requests; however:
  Package python3-requests is not configured yet.

dpkg: error processing package python3-cupshelpers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python3; however:
  Package python3 is not configured yet.
 update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.4); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3; however:
  Package python3 is not configured yet.
 python3-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.

dpkg: error processing package python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-urllib3:
 python3-urllib3 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-urllib3 depends on python3-six; however:
  Package python3-six is not configured yet.

dpkg: error processing package python3-urllib3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-reportlab-accel:amd64:
 python3-reportlab-accel:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-reportlab-accel:amd64 depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-reportlab-accel:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 python3
 update-notifier-common
 python3-lxml
 usb-creator-gtk
 python3-brlapi
 python3-mako
 python3-commandnotfound
 printer-driver-postscript-hp
 language-selector-common
 printer-driver-foo2zjs-common
 python3-update-manager
 system-config-printer-gnome
 python3-six
 openprinting-ppds
 apparmor
 python3-aptdaemon.gtk3widgets
 apturl
 command-not-found
 hplip-data
 python3-pkg-resources
 ubuntu-release-upgrader-core
 python3-bs4
 python3-apport
 gnome-terminal
 python3-problem-report
 python3-reportlab
 python3-feedparser
 ubuntu-drivers-common
 python3-uno
 ibus
 software-properties-gtk
 apturl-common
 python3-pexpect
 python3-chardet
 python3-aptdaemon
 xdiagnose
 update-notifier
 python3-html5lib
 aptdaemon
 ubuntu-desktop
 python3-httplib2
 unattended-upgrades
 gedit
 python3-requests
 printer-driver-foo2zjs
 python3-cupshelpers
 update-manager
 python3-gdbm:amd64
 python3-software-properties
 python3-urllib3
 python3-reportlab-accel:amd64
Processing was halted because there were too many errors.


```

---

### Post by Frogs Hair on 2015-05-02
Try the same with this command. ```
sudo apt-get -f install 
```

---

### Post by xmbwd on 2015-05-02
Thank you.  Same exact error list again.  Eesh.  

> **Frogs Hair said:**
> Try the same with this command. ```
sudo apt-get -f install 
```

---

### Post by Frogs Hair on 2015-05-02
```
Setting up python3 (3.4.3-1)
```

I'm seeing python 2.7.9-1 on 15.04, was there any ppa software installed prior to update ? PPA software sources are disabled prior to upgrade, but the packages are not removed and if python was upgraded manually or via ppa that would bork the upgrade.

---

### Post by xmbwd on 2015-05-02
Yes, I had installed software via ppa before the upgrade. I **did install python3** for testing.  I don't remember if it was via ppa.  I had no idea that would render the computer un-upgradable. :confused:

Is there any way to fix this?  In one of the prior attempts, I tried removing python3 -- but that removed A LOT OF OTHER programs that rendered the partition unusable.

Any suggestions?  If necessary, I can revert back to 14.10 easily enough and make any changes you suggest.  But I don't want to do a completely clean install if I can avoid it.

> **Frogs Hair said:**
> ```
Setting up python3 (3.4.3-1)
```

I'm seeing python 2.7.9-1 on 15.04, was there any ppa software installed prior to update ? PPA software sources are disabled prior to upgrade, but the packages are not removed and if python was upgraded manually or via ppa that would bork the upgrade.

---

### Post by Frogs Hair on 2015-05-02
With the package system tied up the way it is it may by quicker to back up your files if possible and preform a clean installation. I'm not sure you can remove or install packages the way things are. You can also wait for feedback from others but, as of now you can't configure or fix the installation with the basic commands you've tried .That doesn't mean it can't be done though.

---

### Post by xmbwd on 2015-05-02
Ok.  I appreciate the help and suggestions.  I will wait a bit to see if anyone else has a brilliant workaround.  The system is operating perfectly so far.  Just can't upgrade anything.  

Thanks again.  

> **Frogs Hair said:**
> With the package system tied up the way it is it may by quicker to back up your files if possible and preform a clean installation. I'm not sure you can remove or install packages the way things are. You can also wait for feedback from others but, as of now you can't configure or fix the installation with the basic commands you've tried .That doesn't mean it can't be done though.

---

### Post by sandyd on 2015-05-03
This: [https://bugs.launchpad.net/ubuntu/+source/python3-defaults/+bug/1024204/](https://bugs.launchpad.net/ubuntu/+source/python3-defaults/+bug/1024204/)

Possible fix:
Do as it says and install rhythmbox-plugin-magnatune

---

### Post by xmbwd on 2015-05-03
Thanks -- I tried that, and failed.  I tried both using apt-get and Ubuntu Software Center.  

Apt-get throws this error:

```
sudo apt-get install rhythmbox-plugin-magnatune 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 rhythmbox-plugin-magnatune : Depends: rhythmbox (= 3.1-1ubuntu3) but 3.2.0-1~ppafossfreedomutopicubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

> **sandyd said:**
> This: [https://bugs.launchpad.net/ubuntu/+source/python3-defaults/+bug/1024204/](https://bugs.launchpad.net/ubuntu/+source/python3-defaults/+bug/1024204/)

Possible fix:
Do as it says and install rhythmbox-plugin-magnatune

---

### Post by sandyd on 2015-05-03
Aha!

I see the problem now. You have a PPA that's causing a conflict. Since the package versions are possibly ahead of vivid's, its causing a few issues.

It should be fixable.

Can you post the output of
```

ls -l /etc/apt/sources.list.d
```

---

### Post by xmbwd on 2015-05-03
That would be awesome!  Here you go.  I am anticipating reprobation for all the ppas...

```
ls -l /etc/apt/sources.list.d
total 32
-rw-r--r-- 1 root root   0 Apr 26 18:13 atareao-ubuntu-nautilus-extensions-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:13 atareao-ubuntu-nautilus-extensions-utopic.list.save
-rw-r--r-- 1 root root   0 Jan  9 18:06 florian-will-ubuntu-grilo-rb-utopic.list
-rw-r--r-- 1 root root   0 Jan  9 18:06 florian-will-ubuntu-grilo-rb-utopic.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:13 fossfreedom-ubuntu-rhythmbox-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:13 fossfreedom-ubuntu-rhythmbox-utopic.list.save
-rw-r--r-- 1 root root 178 May  2 13:25 google-chrome.list
-rw-r--r-- 1 root root 178 May  2 13:25 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 177 Apr 30 08:33 google-chrome.list.save
-rw-r--r-- 1 root root   0 Oct 30  2014 gstreamer-developers-ppa-utopic.list
-rw-r--r-- 1 root root   0 Oct 30  2014 gstreamer-developers-ppa-utopic.list.save
-rw-r--r-- 1 root root   0 Feb 10 19:31 indicator-brightness-ubuntu-ppa-utopic.list
-rw-r--r-- 1 root root   0 Feb 10 19:31 indicator-brightness-ubuntu-ppa-utopic.list.save
-rw-r--r-- 1 root root   0 Oct 30  2014 ingo-ubuntu-ios7support-utopic.list
-rw-r--r-- 1 root root   0 Oct 30  2014 ingo-ubuntu-ios7support-utopic.list.save
-rw-r--r-- 1 root root   0 Feb 25 14:03 michael-astrapi-ubuntu-ppa-utopic.list
-rw-r--r-- 1 root root   0 Feb 25 14:03 michael-astrapi-ubuntu-ppa-utopic.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:13 nemh-ubuntu-systemback-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:13 nemh-ubuntu-systemback-utopic.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:13 nuvola-player-builders-ubuntu-stable-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:13 nuvola-player-builders-ubuntu-stable-utopic.list.save
-rw-r--r-- 1 root root 250 May  2 13:25 opera.list
-rw-r--r-- 1 root root 250 May  2 13:25 opera.list.distUpgrade
-rw-r--r-- 1 root root 250 Apr 30 08:33 opera.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:14 pipelight-stable-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:14 pipelight-stable-utopic.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:13 qos-ubuntu-pulseaudio-dlna-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:13 qos-ubuntu-pulseaudio-dlna-utopic.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:14 ravefinity-project-ubuntu-ppa-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:14 ravefinity-project-ubuntu-ppa-utopic.list.save
-rw-r--r-- 1 root root   0 Oct 30  2014 relan-exfat-utopic.list
-rw-r--r-- 1 root root   0 Oct 30  2014 relan-exfat-utopic.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:13 scrapy.list
-rw-r--r-- 1 root root   0 Apr 26 18:13 scrapy.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:14 stefansundin-ubuntu-truecrypt-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:14 stefansundin-ubuntu-truecrypt-utopic.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:14 team-xbmc-ubuntu-ppa-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:14 team-xbmc-ubuntu-ppa-utopic.list.save
-rw-r--r-- 1 root root   0 Apr 26 18:13 tiliado-nuvolaplayer.list
-rw-r--r-- 1 root root   0 Apr 26 18:13 tiliado-nuvolaplayer.list.save
-rw-r--r-- 1 root root   0 Oct 30  2014 tualatrix-ppa-utopic.list
-rw-r--r-- 1 root root   0 Oct 30  2014 tualatrix-ppa-utopic.list.save
-rw-r--r-- 1 root root 168 May  2 13:25 webupd8team-ubuntu-java-utopic.list
-rw-r--r-- 1 root root 136 May  2 13:25 webupd8team-ubuntu-java-utopic.list.distUpgrade
-rw-r--r-- 1 root root   0 Apr 26 18:14 yorba-daily-builds-utopic.list
-rw-r--r-- 1 root root   0 Apr 26 18:14 yorba-daily-builds-utopic.list.save


```

---

### Post by sandyd on 2015-05-03
Try
```

sudo apt-get install ppa-purge
ppa-purge ppa:fossfreedom/rhythmbox
```

Might be a few errors, if there are, post back :)

---

### Post by xmbwd on 2015-05-03
I appreciate the help.  Here is what was returned:

```
sudo ppa-purge ppa:fossfreedom/rhythmbox
Updating packages lists
PPA to be removed: fossfreedom rhythmbox
Warning:  Could not find package list for PPA: fossfreedom rhythmbox


```

The list of sources from ```
ls -l /etc/apt/sources.list.d
``` is from 14.10.  At present, no ppas are listed in my source list in Ubuntu Software Center.

---

### Post by sandyd on 2015-05-03
There is something odd going on. Ubuntu is trying to install 3.2.0-1~ppafossfreedomutopicubuntu1 yet the ppa is disabled.

Did you have an upgrade before this?

Can you post the output of
```

apt-cache showpkg rhythmbox
```

Edit:
Actually, wait a second, are you running all of this on your 14.10 installation or your 15.04 installation, this should be all run on your 14.10 installation before upgrade, though it is still fixable without having you to go do the upgrade again.

---

### Post by xmbwd on 2015-05-03
So I am in 15.04 -- and all of the commands I've run are in 15.04.  I have not reverted to 14.10 via my backup.  It sounds like you are saying that I need to go back to 14.10, correct?

Just in case, here is the result:

```
apt-cache showpkg rhythmbox
Package: rhythmbox
Versions: 
3.2.0-1~ppafossfreedomutopicubuntu1 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_vivid_main_binary-amd64_Packages
                  MD5: 263e21c49721f582dd2ee234ff4fedb7
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_vivid_main_i18n_Translation-en
                  MD5: 263e21c49721f582dd2ee234ff4fedb7

3.1-1ubuntu3 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_vivid_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_vivid_main_binary-amd64_Packages
                  MD5: 263e21c49721f582dd2ee234ff4fedb7
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_vivid_main_i18n_Translation-en
                  MD5: 263e21c49721f582dd2ee234ff4fedb7


Reverse Depends: 
  rhythmbox-data,rhythmbox 2.90.1~git20111117.f101562-1
  rhythmbox-data,rhythmbox 2.90.1~git20111117.f101562-1
  rhythmbox-data,rhythmbox
  cinnamon-settings-daemon:i386,rhythmbox 0.11.5
  unity-settings-daemon:i386,rhythmbox 0.11.5
  rhythmbox-plugins:i386,rhythmbox 0.12.6-4
  rhythmbox-plugins:i386,rhythmbox 0.12.6-4
  rhythmbox-plugin-cdrecorder:i386,rhythmbox 0.12.6-4
  rhythmbox-plugin-cdrecorder:i386,rhythmbox 0.12.6-4
  rhythmbox-mozilla:i386,rhythmbox 2.95.5
  rhythmbox-mozilla:i386,rhythmbox 2.95.5
  rhythmbox:i386,rhythmbox
  nautilus:i386,rhythmbox 0.12
  gvfs-daemons:i386,rhythmbox 0.12.6-2
  gvfs:i386,rhythmbox 0.12.6-2
  ubuntukylin-desktop,rhythmbox
  ubuntu-mate-desktop,rhythmbox
  ubuntu-gnome-desktop,rhythmbox
  tangerine-dbg,rhythmbox
  tangerine,rhythmbox
  rhythmbox-radio-browser,rhythmbox
  rhythmbox-plugin-visualizer,rhythmbox 3.1-1ubuntu3
  rhythmbox-ampache,rhythmbox
  gnome-osd,rhythmbox 0.8.8
  gnome-icon-theme-full,rhythmbox 0.12.8
  gnome-do-plugins,rhythmbox
  gnome,rhythmbox 2.96
  cinnamon-settings-daemon,rhythmbox 0.11.5
  cinnamon-desktop-environment,rhythmbox
  unity-settings-daemon,rhythmbox 0.11.5
  ubuntu-desktop,rhythmbox
  rhythmbox-plugins,rhythmbox 0.12.6-4
  rhythmbox-plugins,rhythmbox 0.12.6-4
  rhythmbox-plugins,rhythmbox 3.1-1ubuntu3
  rhythmbox-plugin-zeitgeist,rhythmbox 2.95.5
  rhythmbox-plugin-zeitgeist,rhythmbox 2.95.5
  rhythmbox-plugin-zeitgeist,rhythmbox 3.2
  rhythmbox-plugin-zeitgeist,rhythmbox 3.1-1ubuntu3
  rhythmbox-plugin-magnatune,rhythmbox 3.1-1ubuntu3
  rhythmbox-plugin-cdrecorder,rhythmbox 0.12.6-4
  rhythmbox-plugin-cdrecorder,rhythmbox 0.12.6-4
  rhythmbox-plugin-cdrecorder,rhythmbox 3.1-1ubuntu3
  rhythmbox-mozilla,rhythmbox 2.95.5
  rhythmbox-mozilla,rhythmbox 2.95.5
  rhythmbox-mozilla,rhythmbox 3.1-1ubuntu3
  rhythmbox-dbg,rhythmbox 3.1-1ubuntu3
  rhythmbox-data,rhythmbox 2.90.1~git20111117.f101562-1
  rhythmbox-data,rhythmbox 2.90.1~git20111117.f101562-1
  rhythmbox-data,rhythmbox
  nautilus,rhythmbox 0.12
  gvfs-daemons,rhythmbox 0.12.6-2
  gvfs,rhythmbox 0.12.6-2
  gnome-icon-theme,rhythmbox 0.12.8
Dependencies: 
3.2.0-1~ppafossfreedomutopicubuntu1 - libc6 (2 2.14) libglib2.0-0 (2 2.34.0) libgstreamer-plugins-base1.0-0 (2 1.0.0) libgstreamer1.0-0 (2 1.4.0) libgtk-3-0 (2 3.0.0) libpeas-1.0-0 (2 1.0.0) librhythmbox-core9 (5 3.2.0-1~ppafossfreedomutopicubuntu1) libtotem-plparser18 (2 3.10.0) libx11-6 (0 (null)) python3 (2 3.4~) python3 (3 3.5) python3.4 (0 (null)) rhythmbox-data (5 3.2.0-1~ppafossfreedomutopicubuntu1) dbus (0 (null)) gstreamer1.0-plugins-base (2 1.0.6) gstreamer1.0-plugins-good (2 1.0.6) gnome-icon-theme (0 (null)) gstreamer1.0-x (0 (null)) media-player-info (0 (null)) gir1.2-rb-3.0 (5 3.2.0-1~ppafossfreedomutopicubuntu1) gir1.2-glib-2.0 (0 (null)) gir1.2-gtk-3.0 (0 (null)) python-gi (0 (null)) gstreamer1.0-plugins-bad (0 (null)) gstreamer1.0-plugins-ugly (0 (null)) gnome-codec-install (0 (null)) gnome-control-center (0 (null)) yelp (0 (null)) avahi-daemon (0 (null)) notification-daemon (0 (null)) gstreamer1.0-pulseaudio (0 (null)) gvfs-backends (0 (null)) rhythmbox-plugins (0 (null)) rhythmbox-mozilla (0 (null)) rhythmbox-plugin-cdrecorder (0 (null)) rhythmbox-plugin-zeitgeist (0 (null)) rhythmbox-plugin-visualizer (0 (null)) gvfs (3 1.4.1-6) gvfs:i386 (3 1.4.1-6) rhythmbox:i386 (0 (null)) 
3.1-1ubuntu3 - libc6 (2 2.14) libglib2.0-0 (2 2.34.0) libgstreamer-plugins-base1.0-0 (2 1.0.0) libgstreamer1.0-0 (2 1.4.0) libgtk-3-0 (2 3.0.0) libpeas-1.0-0 (2 1.0.0) librhythmbox-core8 (5 3.1-1ubuntu3) libtotem-plparser18 (2 3.10.0) libx11-6 (0 (null)) python3 (3 3.5) python3 (2 3.4~) python3.4 (0 (null)) rhythmbox-data (5 3.1-1ubuntu3) dbus (0 (null)) gstreamer1.0-plugins-base (2 1.0.6) gstreamer1.0-plugins-good (2 1.0.6) adwaita-icon-theme (0 (null)) gstreamer1.0-x (0 (null)) media-player-info (0 (null)) gir1.2-rb-3.0 (5 3.1-1ubuntu3) gir1.2-glib-2.0 (0 (null)) gir1.2-gtk-3.0 (0 (null)) python3-gi (0 (null)) gstreamer1.0-plugins-bad (0 (null)) gstreamer1.0-plugins-ugly (0 (null)) gnome-codec-install (0 (null)) gnome-control-center (0 (null)) yelp (0 (null)) avahi-daemon (0 (null)) notification-daemon (0 (null)) gstreamer1.0-pulseaudio (0 (null)) gvfs-backends (0 (null)) rhythmbox-plugins (0 (null)) rhythmbox-mozilla (0 (null)) rhythmbox-plugin-cdrecorder (0 (null)) rhythmbox-plugin-zeitgeist (0 (null)) gvfs (3 1.4.1-6) gvfs:i386 (3 1.4.1-6) rhythmbox:i386 (0 (null)) 
Provides: 
3.2.0-1~ppafossfreedomutopicubuntu1 - 
3.1-1ubuntu3 - 
Reverse Provides: 


```

> **sandyd said:**
> There is something odd going on. Ubuntu is trying to install 3.2.0-1~ppafossfreedomutopicubuntu1 yet the ppa is disabled.

Did you have an upgrade before this?

Can you post the output of
```

apt-cache showpkg rhythmbox
```

Edit:
Actually, wait a second, are you running all of this on your 14.10 installation or your 15.04 installation, this should be all run on your 14.10 installation before upgrade, though it is still fixable without having you to go do the upgrade again.

---

### Post by sandyd on 2015-05-03
Lets give this a try...
```

sudo apt-get install rhythmbox=3.1-1ubuntu3 rhythmbox-data=3.1-1ubuntu3 gir1.2-rb-3.0=3.1-1ubuntu3
```

---

### Post by xmbwd on 2015-05-03
Unfortunately, I got this back (again, I am on the 15.04 install):

```
sudo apt-get install rhythmbox=3.1-1ubuntu3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 rhythmbox : Depends: rhythmbox-data (= 3.1-1ubuntu3) but 3.2.0-1~ppafossfreedomutopicubuntu1 is to be installed
             Depends: gir1.2-rb-3.0 (= 3.1-1ubuntu3) but it is not going to be installed
             Recommends: rhythmbox-plugins but it is not going to be installed
             Recommends: rhythmbox-mozilla but it is not going to be installed
             Recommends: rhythmbox-plugin-cdrecorder but it is not going to be installed
             Recommends: rhythmbox-plugin-zeitgeist but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by sandyd on 2015-05-03
A few more packages to reverse it seems
Run
```

dpkg -l | grep rhythmbox
```

---

### Post by xmbwd on 2015-05-03
That yields:  

```
dpkg -l | grep rhythmbox
ii  gir1.2-rb-3.0                                        3.2.0-1~ppafossfreedomutopicubuntu1        amd64        GObject introspection data for the rhythmbox music player
ii  librhythmbox-core9                                   3.2.0-1~ppafossfreedomutopicubuntu1        amd64        support library for the rhythmbox music player
rc  rhythmbox                                            3.2.0-1~ppafossfreedomutopicubuntu1        amd64        music player and organizer for GNOME
ii  rhythmbox-data                                       3.2.0-1~ppafossfreedomutopicubuntu1        all          data files for rhythmbox

```

---

### Post by sandyd on 2015-05-03
Do
```

sudo apt-get install rhythmbox=3.1-1ubuntu3 rhythmbox-data=3.1-1ubuntu3 gir1.2-rb-3.0=3.1-1ubuntu3 rhythmbox-plugin-magnatune
```

---

### Post by xmbwd on 2015-05-03
It seemed to make some progress in the beginning, but ended with the same error:

```
sudo apt-get install rhythmbox=3.1-1ubuntu3 rhythmbox-data=3.1-1ubuntu3 gir1.2-rb-3.0=3.1-1ubuntu3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  librhythmbox-core8 rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-zeitgeist rhythmbox-plugins
Suggested packages:
  gnome-control-center
The following packages will be REMOVED:
  librhythmbox-core9
The following NEW packages will be installed:
  librhythmbox-core8 rhythmbox rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-zeitgeist rhythmbox-plugins
The following packages will be DOWNGRADED:
  gir1.2-rb-3.0 rhythmbox-data
0 upgraded, 6 newly installed, 2 downgraded, 1 to remove and 0 not upgraded.
93 not fully installed or removed.
Need to get 1,328 kB of archives.
After this operation, 7,101 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid/main gir1.2-rb-3.0 amd64 3.1-1ubuntu3 [37.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ vivid/main librhythmbox-core8 amd64 3.1-1ubuntu3 [481 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ vivid/main rhythmbox-data all 3.1-1ubuntu3 [386 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ vivid/main rhythmbox amd64 3.1-1ubuntu3 [124 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ vivid/main rhythmbox-mozilla amd64 3.1-1ubuntu3 [5,552 B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ vivid/main rhythmbox-plugin-cdrecorder amd64 3.1-1ubuntu3 [14.3 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ vivid/main rhythmbox-plugin-zeitgeist all 3.1-1ubuntu3 [56.5 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ vivid/main rhythmbox-plugins amd64 3.1-1ubuntu3 [223 kB]
Fetched 1,328 kB in 3s (424 kB/s)          
dpkg: warning: downgrading gir1.2-rb-3.0 from 3.2.0-1~ppafossfreedomutopicubuntu1 to 3.1-1ubuntu3
(Reading database ... 335347 files and directories currently installed.)
Preparing to unpack .../gir1.2-rb-3.0_3.1-1ubuntu3_amd64.deb ...
Unpacking gir1.2-rb-3.0 (3.1-1ubuntu3) over (3.2.0-1~ppafossfreedomutopicubuntu1) ...
(Reading database ... 335345 files and directories currently installed.)
Removing librhythmbox-core9 (3.2.0-1~ppafossfreedomutopicubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Selecting previously unselected package librhythmbox-core8.
(Reading database ... 335335 files and directories currently installed.)
Preparing to unpack .../librhythmbox-core8_3.1-1ubuntu3_amd64.deb ...
Unpacking librhythmbox-core8 (3.1-1ubuntu3) ...
dpkg: warning: downgrading rhythmbox-data from 3.2.0-1~ppafossfreedomutopicubuntu1 to 3.1-1ubuntu3
Preparing to unpack .../rhythmbox-data_3.1-1ubuntu3_all.deb ...
Unpacking rhythmbox-data (3.1-1ubuntu3) over (3.2.0-1~ppafossfreedomutopicubuntu1) ...
Selecting previously unselected package rhythmbox.
Preparing to unpack .../rhythmbox_3.1-1ubuntu3_amd64.deb ...
Unpacking rhythmbox (3.1-1ubuntu3) ...
Selecting previously unselected package rhythmbox-mozilla.
Preparing to unpack .../rhythmbox-mozilla_3.1-1ubuntu3_amd64.deb ...
Unpacking rhythmbox-mozilla (3.1-1ubuntu3) ...
Selecting previously unselected package rhythmbox-plugin-cdrecorder.
Preparing to unpack .../rhythmbox-plugin-cdrecorder_3.1-1ubuntu3_amd64.deb ...
Unpacking rhythmbox-plugin-cdrecorder (3.1-1ubuntu3) ...
Selecting previously unselected package rhythmbox-plugin-zeitgeist.
Preparing to unpack .../rhythmbox-plugin-zeitgeist_3.1-1ubuntu3_all.deb ...
Unpacking rhythmbox-plugin-zeitgeist (3.1-1ubuntu3) ...
Selecting previously unselected package rhythmbox-plugins.
Preparing to unpack .../rhythmbox-plugins_3.1-1ubuntu3_amd64.deb ...
Unpacking rhythmbox-plugins (3.1-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.44.0-1ubuntu3) ...
Processing triggers for libglib2.0-0:amd64 (2.44.0-1ubuntu3) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up librhythmbox-core8 (3.1-1ubuntu3) ...
Setting up gir1.2-rb-3.0 (3.1-1ubuntu3) ...
Setting up rhythmbox-data (3.1-1ubuntu3) ...
Setting up python3 (3.4.3-1) ...
running python rtupdate hooks for python3.4...
dpkg-query: package 'rhythmbox-plugin-magnatune' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-magnatune
error running python rtupdate hook rhythmbox-plugin-magnatune
dpkg: error processing package python3 (--configure):
 subprocess installed post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python3; however:
  Package python3 is not configured yet.
 language-selector-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 language-selector-common depends on python3-apt (>= 0.7.12.0); however:
  Package python3-apt is not configured yet.

dpkg: error processing package language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3; however:
  Package python3 is not configured yet.
 ubuntu-drivers-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 ubuntu-drivers-common depends on python3-apt; however:
  Package python3-apt is not configured yet.

dpkg: error processing package ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python3:any; however:
  Package python3 is not configured yet.
 update-notifier-common depends on python3-apt; however:
  Package python3-apt is not configured yet.

dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.4); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-commandnotfound:
 python3-commandnotfound depends on python3-apt; however:
  Package python3-apt is not configured yet.
 python3-commandnotfound depends on python3-gdbm; however:
  Package python3-gdbm:amd64 is not configured yet.
 python3-commandnotfound depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-commandnotfound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of command-not-found:
 command-not-found depends on python3-commandnotfound (>= 0.3ubuntu7); however:
  Package python3-commandnotfound is not configured yet.

dpkg: error processing package command-not-found (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-distupgrade depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.

dpkg: error processing package python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-update-manager depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing package python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3; however:
  Package python3 is not configured yet.
 ubuntu-release-upgrader-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:15.04.14); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing package ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ufw:
 ufw depends on python3; however:
  Package python3 is not configured yet.
 ufw depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ufw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3; however:
  Package python3 is not configured yet.
 update-manager-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 update-manager-core depends on python3-update-manager (= 1:15.04.7); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing package update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl-common:
 apturl-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 apturl-common depends on python3-apt; however:
  Package python3-apt is not configured yet.
 apturl-common depends on python3-update-manager; however:
  Package python3-update-manager is not configured yet.

dpkg: error processing package apturl-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on python3; however:
  Package python3 is not configured yet.
 unattended-upgrades depends on python3-apt; however:
  Package python3-apt is not configured yet.

dpkg: error processing package unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3; however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3-apt (>= 0.6.20ubuntu16); however:
  Package python3-apt is not configured yet.
 python3-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.

dpkg: error processing package python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3; however:
  Package python3 is not configured yet.
 software-properties-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 software-properties-common depends on python3-software-properties (= 0.96.4); however:
  Package python3-software-properties is not configured yet.

dpkg: error processing package software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3:any (>= 3.4); however:
  Package python3 is not configured yet.
 python3-pkg-resources depends on python3:any (<< 3.5); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon:
 python3-aptdaemon depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon depends on python3-apt (>= 0.8.5~ubuntu1); however:
  Package python3-apt is not configured yet.
 python3-aptdaemon depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.

dpkg: error processing package python3-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon.gtk3widgets:
 python3-aptdaemon.gtk3widgets depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon.gtk3widgets depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package python3-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3; however:
  Package python3 is not configured yet.
 software-properties-gtk depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 software-properties-gtk depends on python3-software-properties (= 0.96.4); however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not configured yet.
 software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.75); however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing package software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on python3; however:
  Package python3 is not configured yet.
 apturl depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 apturl depends on apturl-common (= 0.5.2ubuntu6); however:
  Package apturl-common is not configured yet.
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
 apturl depends on python3-aptdaemon; however:
  Package python3-aptdaemon is not configured yet.
 apturl depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.

dpkg: error processing package apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
  Package update-notifier-common is not configured yet.

dpkg: error processing package flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of foomatic-db-compressed-ppds:
 foomatic-db-compressed-ppds depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package foomatic-db-compressed-ppds (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-ibus-1.0:amd64:
 gir1.2-ibus-1.0:amd64 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package gir1.2-ibus-1.0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on python3; however:
  Package python3 is not configured yet.
 gnome-menus depends on python3:any (>= 3.1~); however:
  Package python3 is not configured yet.

dpkg: error processing package gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-brlapi:
 python3-brlapi depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-brlapi depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-brlapi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-cairo:
 python3-cairo depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-cairo depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-cairo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pyatspi:
 python3-pyatspi depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pyatspi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-speechd:
 python3-speechd depends on python3; however:
  Package python3 is not configured yet.
 python3-speechd depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-speechd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-orca:
 gnome-orca depends on python3; however:
  Package python3 is not configured yet.
 gnome-orca depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 gnome-orca depends on python3-brlapi (>= 0.5.1); however:
  Package python3-brlapi is not configured yet.
 gnome-orca depends on python3-cairo; however:
  Package python3-cairo is not configured yet.
 gnome-orca depends on python3-pyatspi (>= 2.10); however:
  Package python3-pyatspi is not configured yet.
 gnome-orca depends on python3-speechd (>= 0.8); however:
  Package python3-speechd is not configured yet.

dpkg: error processing package gnome-orca (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon.pkcompat:
 python3-aptdaemon.pkcompat depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon.pkcompat depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package python3-aptdaemon.pkcompat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer1.0-packagekit:
 gstreamer1.0-packagekit depends on python3-aptdaemon.pkcompat | packagekit-system-interface | packagekit (= 0.8.17-4ubuntu4); however:
  Package python3-aptdaemon.pkcompat is not configured yet.
  Package packagekit-system-interface is not installed.
  Package python3-aptdaemon.pkcompat which provides packagekit-system-interface is not configured yet.
  Package packagekit is not installed.

dpkg: error processing package gstreamer1.0-packagekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip-data:
 hplip-data depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package hplip-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pil:amd64:
 python3-pil:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-pil:amd64 depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pil:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pexpect:
 python3-pexpect depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pexpect (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-reportlab-accel:amd64:
 python3-reportlab-accel:amd64 depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-reportlab-accel:amd64 depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-reportlab-accel:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-reportlab:
 python3-reportlab depends on python3-reportlab-accel (>= 3.1.44-1); however:
  Package python3-reportlab-accel:amd64 is not configured yet.
 python3-reportlab depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-reportlab (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on hplip-data (= 3.15.2-0ubuntu4); however:
  Package hplip-data is not configured yet.
 hplip depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 hplip depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 hplip depends on python3-pil; however:
  Package python3-pil:amd64 is not configured yet.
 hplip depends on python3-pexpect; however:
  Package python3-pexpect is not configured yet.
 hplip depends on python3-reportlab; however:
  Package python3-reportlab is not configured yet.

dpkg: error processing package hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on python3; however:
  Package python3 is not configured yet.
 printer-driver-postscript-hp depends on hplip (>= 3.15.2-0ubuntu4); however:
  Package hplip is not configured yet.

dpkg: error processing package printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus:
 ibus depends on gir1.2-ibus-1.0 (= 1.5.9-1ubuntu3); however:
  Package gir1.2-ibus-1.0:amd64 is not configured yet.
 ibus depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ibus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus-table:
 ibus-table depends on ibus (>= 1.5.0); however:
  Package ibus is not configured yet.
 ibus-table depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ibus-table (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing package kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k4dirstat:
 k4dirstat depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package k4dirstat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python3; however:
  Package python3 is not configured yet.
 aptdaemon depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 aptdaemon depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Errors were encountered while processing:
 python3
 python3-apt
 language-selector-common
 ubuntu-drivers-common
 update-notifier-common
 ubuntu-minimal
 apparmor
 python3-gdbm:amd64
 python3-commandnotfound
 command-not-found
 python3-distupgrade
 python3-update-manager
 ubuntu-release-upgrader-core
 ubuntu-standard
 ufw
 update-manager-core
 apturl-common
 unattended-upgrades
 python3-software-properties
 software-properties-common
 python3-pkg-resources
 python3-aptdaemon
 python3-aptdaemon.gtk3widgets
 software-properties-gtk
 apturl
 flashplugin-installer
 foomatic-db-compressed-ppds
 gedit
 gir1.2-ibus-1.0:amd64
 gnome-menus
 python3-brlapi
 python3-cairo
 python3-pyatspi
 python3-speechd
 gnome-orca
 gnome-terminal
 python3-aptdaemon.pkcompat
 gstreamer1.0-packagekit
 hplip-data
 python3-pil:amd64
 python3-pexpect
 python3-reportlab-accel:amd64
 python3-reportlab
 hplip
 printer-driver-postscript-hp
 ibus
 ibus-table
 kde-runtime
 k4dirstat
 kdepim-runtime
 aptdaemon
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thank you again.  I'll keep trying if you still have ideas.

---

### Post by sandyd on 2015-05-03
Fixed the command since it's working now.

---

### Post by xmbwd on 2015-05-03
Ran with new command: 

```
sudo apt-get install rhythmbox=3.1-1ubuntu3 rhythmbox-data=3.1-1ubuntu3 gir1.2-rb-3.0=3.1-1ubuntu3 rhythmbox-plugin-magnatune
```

*And it worked!!!!!*   I ran update, upgrade, autoremove, and autoclean to test and all came back with 0 errors and 0 tasks.  

Thank you, **_really_**, for helping me through this.  Much, much, much appreciation.  :p

I will mark this solved.  Again, thank you!!!

> **sandyd said:**
> Fixed the command since it's working now.

---

### Post by sandyd on 2015-05-03
No problem :)

---

