---
title: "dpkg: error"
date: 2008-01-18
forum: General Help
---

### Post by dan0z on 2008-01-18
Hi,

I am i bit mythed with this one, i have just reinstalled Ubuntu v7.04, once installed ran the update and received loads of errors, have tried to run apt-get dist-upgrade and now get lots of errors (see below) any ideas as to why I am getting these errors on a fresh install and any solutions would be great.

Thanks

Dan

Error:

root@uberserv:/home/dan# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up capplets-data (2.18.1-0ubuntu2.1) ...
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.18); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.19); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-media-common (2.18.0-0ubuntu1.1) ...
dpkg: error processing gnome-media-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libgnome-media0:
 libgnome-media0 depends on gnome-media-common (>= 2.18); however:
  Package gnome-media-common is not configured yet.
 libgnome-media0 depends on gnome-media-common (<< 2.19); however:
  Package gnome-media-common is not configured yet.
dpkg: error processing libgnome-media0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on libgnome-media0; however:
  Package libgnome-media0 is not configured yet.
 gnome-media depends on gnome-media-common (>= 2.18); however:
  Package gnome-media-common is not configured yet.
 gnome-media depends on gnome-media-common (<< 2.19); however:
  Package gnome-media-common is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Setting up tomboy (0.6.3-0ubuntu1.1) ...
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-system-tools (2.18.1-0ubuntu2) ...
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 capplets-data
 gnome-control-center
 gnome-media-common
 libgnome-media0
 gnome-media
 gnome-panel-data
 gnome-panel
 tomboy
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@uberserv:/home/dan#

---

### Post by markharding557 on 2008-01-18
try using update manager,this should change the apt sources list for you.
when using apt-dist-upgrade you have to change the sources yourself,your read out indicates that your sources have not been changed 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by dan0z on 2008-01-18
I had tried to run an update but said there were no updates, but i had failed to notice the upgrade button :/

I have upgraded now and all seems ok.

Thanks

dan

---

