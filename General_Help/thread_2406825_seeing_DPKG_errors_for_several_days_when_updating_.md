---
title: "seeing DPKG errors for several days when updating 18.04"
date: 2018-11-26
forum: General Help
---

### Post by Cavsfan on 2018-11-26
For the last week I have been getting errors when manually updating and the normal steps to resolve broken packages does not work.
This is what I get:
```
root@cavsfan-xubuntu:/var/lib/apt# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
_10 not fully installed or removed._
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
E: py3compile:183: cannot create directory /usr/share/hplip/ui5/__pycache__: FileNotFoundError(2, 'No such file or directory')
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/cleandialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/cleandialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/colorcaldialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/colorcaldialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devicesetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devicesetupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/deviceuricombobox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr5.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr5_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr_ext.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabgrouptable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabnametable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabwindow.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabwindow_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/faxsetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/faxsetupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/filetable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/firmwaredialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/firmwaredialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/infodialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/infodialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/linefeedcaldialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/linefeedcaldialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/loadpapergroupbox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/makecopiesdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/makecopiesdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/mimetypesdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/mimetypesdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/nodevicesdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/nodevicesdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindiagnose.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindiagnose_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pluginlicensedialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pluginlicensedialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pqdiagdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pqdiagdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printernamecombobox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettings_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettingsdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettingsdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettingstoolbox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printtestpagedialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printtestpagedialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/queuesconf.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/readonlyradiobutton.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/sendfaxdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/sendfaxdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/settingsdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/settingsdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/setupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/setupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/setupdialog_base5.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/systemtray.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/systrayframe.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/systrayframe_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/ui_utils.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/upgradedialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/upgradedialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/wifisetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/wifisetupdialog_base.py'
error running python rtupdate hook hplip-data
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.


dpkg: error processing package ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.6.6-1~); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent processing triggers for gnome-menus:
 gnome-menus depends on python3:any (>= 3.1~); however:
  Package python3 is not configured yet.


dpkg: error processing package gnome-menus (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent configuration of python3-lib2to3:
 python3-lib2to3 depends on python3 (>= 3.6.6-1~); however:
  Package python3 is not configured yet.
 python3-lib2to3 depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-lib2to3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distutils:
 python3-distutils depends on python3 (>= 3.6.6-1~); however:
  Package python3 is not configured yet.
 python3-distutils depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-distutils depends on python3-lib2to3 (>= 3.6.4); however:
  Package python3-lib2to3 is not configured yet.


dpkg: error processing package python3-distutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-distupgrade depends on python3-update-manager (>= 1:0.196.2~); however:
  Package python3-update-manager is not configured yet.


dpkg: error processing package python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent processing triggers for ufw:
 ufw depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package ufw (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on ubuntu-release-upgrader-core (= 1:18.04.29); however:
  Package ubuntu-release-upgrader-core is not configured yet.
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-distupgrade (= 1:18.04.29); however:
  Package python3-distupgrade is not configured yet.


dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 update-manager-core depends on python3-update-manager (= 1:18.04.11.7); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core (>= 1:18.04.9); however:
  Package ubuntu-release-upgrader-core is not configured yet.


dpkg: error processing package update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
Errors were encountered while processing:
 python3
 python3-update-manager
 ubuntu-release-upgrader-core
 update-manager
 python3-gdbm:amd64
 gnome-menus
 python3-lib2to3
 python3-distutils
 python3-distupgrade
 ufw
 ubuntu-release-upgrader-gtk
 update-manager-core
 gconf2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I had installed Xubuntu 18.04 2-3 times after initial release, had these same problems and just deleted the partition. I had been having better luck with this one after the 1st point release.
But, these errors will not go away.

This is what I tried prior to the above message:
```
$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```

---

### Post by #&amp;thj^% on 2018-11-26
HiYa Cavsfan ;)
I have seen customers bring their machines with much the same error seen by yourself:
HP is aware:
> Warning: If you are upgrading HPLIP and HPLIP is already preinstalled with your distribution, or you if you installed HPLIP using an RPM, DEB, or other package, please uninstall the previous version using the method specific for your distribution. **_If you do not do this, you may have package conflict issues or functionality problems._**
Source: [https://developers.hp.com/hp-linux-imaging-and-printing/install/step3/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/step3/index)
The fix i used was to remove completely HPLIP via:
```
sudo apt remove --purge hplip hplip-data hplip-doc hplip-gui hpijs-ppds \
libsane-hpaio printer-driver-hpcups printer-driver-hpijs
sudo rm -rf /usr/share/hplip/

```

And I always run this after a problem reported:
```
sudo apt autoremove
```
If more info is needed have read here: [https://askubuntu.com/questions/1056077/how-to-install-latest-hplip-on-my-ubuntu-to-support-my-hp-printer-and-or-scanner/1056078#1056078](https://askubuntu.com/questions/1056077/how-to-install-latest-hplip-on-my-ubuntu-to-support-my-hp-printer-and-or-scanner/1056078#1056078)

---

### Post by Cavsfan on 2018-11-26
Not sure but, I think I fixed it; at least the errors are gone.

I removed python3 and reinstalled it plus autoremoved a bunch of stuff. 

Have to do some more checking. But, thanks for that tip about the [COLOR=#000000]*HPLIP*[/COLOR] package. I'll do that too.

I think removing python3 may have removed more than I wanted. I'll do some more investigation before I reboot.

---

### Post by Cavsfan on 2018-11-26
Thanks for trying to save me from myself [COLOR=#000000]**1fallen** and I wish I tried your fix first. :P

Because my solution caused no network and a re-install although with your post I did get my network printer working.

It's not like I haven't done this a couple of times or anything [/COLOR]:lolflag:

Having fun installing or re-installing systems is what I live for. I like having these threads so, when I get the same problem I can refer back to this.

Hopefully I won't have to but, if I do...

Hope things are going better for you than they have been for me lately. :)

---

