---
title: "Cups failure, samba, winbind"
date: 2015-01-24
forum: General Help
---

### Post by Subito_Piano on 2015-01-24
Hi -- I've spent fruitless hours doing a lot of research on this.  CUPS simply stopped working -- it may have been after installig the latest recommended upgrades --- it failed to upgrade two packages, winbind and samba.  Now, I can't connect to localhost:631; when I invoke the printer gui i receive the message "Printing sevice not available. Start the service on this computer or connect to another server."  When i click "connect," the only server option is localhost -- when i try to connect, it fails to conect to server. Attempting to reinstall wnbind and samba, I receive the mesage "dpkg: error processing package samba (--purge): package is in a very bad inconsistent state; you should reinstall it before attempting a removal."  Digging around, it seems that the two issues (corrupted winbind/samba installation and CUPS not starting) may be related; however, i cannot upgrade, downgrade, remove, purge, reinstall or force removal of either winbind or samba through synaptic or commandline.  I've tried ```
sudo dpkg --remove --force-remove-reinstreq winbind
```and```
sudo dpkg --force-all -P samba winbind
```as well as removing the deb packages from /var/cache/apt/archives/ and other suggestions from around the web.  I can't print -- and i HAVE to be able to print.
Followng is the message when trying to reinstall wibind and samba:
```
~$ sudo apt-get --reinstall install samba winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 linux-headers-3.13.0-43-generic linux-image-3.13.0-40-lowlatency
  linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic
  linux-signed-image-3.13.0-43-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  smbldap-tools
The following packages will be upgraded:
  samba winbind
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/1,247 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
/bin/sh: 1: /usr/sbin/dpkg-preconfigure: not found
(Reading database ... 345648 files and directories currently installed.)
Preparing to unpack .../winbind_2%3a4.1.6+dfsg-1ubuntu2.14.04.4_amd64.deb ...
/var/lib/dpkg/info/winbind.prerm: 5: /var/lib/dpkg/info/winbind.prerm: invoke-rc.d: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 5: /var/lib/dpkg/tmp.ci/prerm: invoke-rc.d: not found
dpkg: error processing archive /var/cache/apt/archives/winbind_2%3a4.1.6+dfsg-1ubuntu2.14.04.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/winbind.postinst: 13: /var/lib/dpkg/info/winbind.postinst: invoke-rc.d: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to unpack .../samba_2%3a4.1.6+dfsg-1ubuntu2.14.04.4_amd64.deb ...
/var/lib/dpkg/info/samba.prerm: 10: /var/lib/dpkg/info/samba.prerm: invoke-rc.d: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 10: /var/lib/dpkg/tmp.ci/prerm: invoke-rc.d: not found
dpkg: error processing archive /var/cache/apt/archives/samba_2%3a4.1.6+dfsg-1ubuntu2.14.04.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/samba.postinst: 78: /var/lib/dpkg/info/samba.postinst: invoke-rc.d: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/winbind_2%3a4.1.6+dfsg-1ubuntu2.14.04.4_amd64.deb
 /var/cache/apt/archives/samba_2%3a4.1.6+dfsg-1ubuntu2.14.04.4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Trying to remove or reinstall one package at a time simply doesn't work.  Somehow they are tied together in the package manager's thinking....
Maybe my laptop is simply allergic to 14.04!  ;-) 13.10 gave me no  problems but the last month and a half with this LTS is driving me nuts!   Any help appreciated.
--------
Lenovo S205, Ubuntu Studio 14.04, AMD 64....

---

### Post by Subito_Piano on 2015-01-25
Problem propagating....this does not look good.  [IMG]https://wl.widelands.org/wlmedia/img/smileys/face-shock.png[/IMG]    Lifeline, anyone??!?!  

```
~$ sudo apt-get install reinstall samba
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package reinstall
dad@dad-laptop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
samba set to manually installed.
The following packages were automatically installed and are no longer required:
  lib32gcc1 linux-headers-3.13.0-43-generic linux-image-3.13.0-40-lowlatency
  linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic
  linux-signed-image-3.13.0-43-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
17 not fully installed or removed.
Need to get 0 B/317 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
/bin/sh: 1: /usr/sbin/dpkg-preconfigure: not found
dpkg: error processing package cups-browsed (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package cups-daemon (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Setting up lightdm (1.10.3-0ubuntu2) ...
/var/lib/dpkg/info/lightdm.postinst: 94: /var/lib/dpkg/info/lightdm.postinst: update-rc.d: not found
dpkg: error processing package lightdm (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up network-manager (0.9.8.8-0ubuntu7) ...
/var/lib/dpkg/info/network-manager.postinst: 28: /var/lib/dpkg/info/network-manager.postinst: update-rc.d: not found
dpkg: error processing package network-manager (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Setting up ntp (1:4.2.6.p5+dfsg-3ubuntu2.14.04.1) ...
/var/lib/dpkg/info/ntp.postinst: 22: /var/lib/dpkg/info/ntp.postinst: addgroup: not found
dpkg: error processing package ntp (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Setting up samba (2:4.1.6+dfsg-1ubuntu2.14.04.4) ...
/var/lib/dpkg/info/samba.postinst: 78: /var/lib/dpkg/info/samba.postinst: invoke-rc.d: not found
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntustudio-default-settings:
 ubuntustudio-default-settings depends on lightdm (>= 0.9.3-0ubuntu2); however:
  Package lightdm is not configured yet.

dpkg: error processing package ubuntustudio-default-settings (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up wicd-daemon (1.7.2.4-4.1ubuntu1) ...
/var/lib/dpkg/info/wicd-daemon.postinst: 71: /var/lib/dpkg/info/wicd-daemon.postinst: update-rc.d: not found
dpkg: error processing package wicd-daemon (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba (= 2:4.1.6+dfsg-1ubuntu2.14.04.4); however:
  Package samba is not configured yet.

dpkg: error processing package winbind (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up bind9 (1:9.9.5.dfsg-3ubuntu0.1) ...
/var/lib/dpkg/info/bind9.postinst: 11: /var/lib/dpkg/info/bind9.postinst: addgroup: not found
dpkg: error processing package bind9 (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on cups-daemon (>= 1.7.2-0ubuntu1.2); however:
  Package cups-daemon is not configured yet.

dpkg: error processing package cups-core-drivers (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups:
 cups depends on cups-core-drivers (>= 1.7.2-0ubuntu1.2); however:
  Package cups-core-drivers is not configured yet.
 cups depends on cups-daemon (>= 1.7.2-0ubuntu1.2); however:
  Package cups-daemon is not configured yet.

dpkg: error processing package cups (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up doc-base (0.10.5) ...
/var/lib/dpkg/info/doc-base.postinst: 33: /var/lib/dpkg/info/doc-base.postinst: install-docs: not found
dpkg: error processing package doc-base (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cups (>= 1.1.20); however:
  Package cups is not configured yet.

dpkg: error processing package hplip (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.9.8); however:
  Package network-manager is not configured yet.

dpkg: error processing package network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up unattended-upgrades (0.82.1ubuntu2) ...
/var/lib/dpkg/info/unattended-upgrades.postinst: 65: /var/lib/dpkg/info/unattended-upgrades.postinst: update-rc.d: not found
dpkg: error processing package unattended-upgrades (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of wicd-gtk:
 wicd-gtk depends on wicd-daemon (= 1.7.2.4-4.1ubuntu1); however:
  Package wicd-daemon is not configured yet.

dpkg: error processing package wicd-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 cups-browsed
 cups-daemon
 lightdm
 network-manager
 ntp
 samba
 ubuntustudio-default-settings
 wicd-daemon
 winbind
 bind9
 cups-core-drivers
 cups
 doc-base
 hplip
 network-manager-gnome
 unattended-upgrades
 wicd-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QIII on 2015-01-25
This

```
sudo apt-get install reinstall samba
```

should be

```
sudo apt-get install --reinstall samba
```

That may or may not get you moving.

---

### Post by Subito_Piano on 2015-01-25
I think i tried that -- but did it again.  Output:
```
~$ sudo apt-get install --reinstall samba
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 linux-headers-3.13.0-43-generic linux-image-3.13.0-40-lowlatency
  linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic
  linux-signed-image-3.13.0-43-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
17 not fully installed or removed.
Need to get 0 B/317 kB of archives.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for samba:amd64
```

---

