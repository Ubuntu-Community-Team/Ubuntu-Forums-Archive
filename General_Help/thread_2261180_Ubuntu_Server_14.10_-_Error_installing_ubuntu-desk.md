---
title: "Ubuntu Server 14.10 - Error installing ubuntu-desktop and apt-get upgrade"
date: 2015-01-16
forum: General Help
---

### Post by will63 on 2015-01-16
I'm attempting to become more comfortable with terminal, however some things I just would like to be able to have a gui for.
I attempted to install ubuntu-desktop but the install threw an error.

```
root@ns350871:~# apt-get install ubuntu-desktopReading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-desktop is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
10 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up bluez (4.101-0ubuntu20) ...
start: Job failed to start
invoke-rc.d: initscript bluetooth, action "start" failed.
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                          No apport report written because MaxReports has already been reached
                                                                No apport report written because MaxReports has already been reached
                      No apport report written because MaxReports has already been reached
                                                                                          No apport report written because MaxReports has already been reached
                                                No apport report written because MaxReports has already been reached
      No apport report written because MaxReports has already been reached
                                                                          No apport report written because MaxReports has already been reached
                                dpkg: error processing package bluez (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bluez-alsa:amd64:
 bluez-alsa:amd64 depends on bluez; however:
  Package bluez is not configured yet.


dpkg: error processing package bluez-alsa:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.


dpkg: error processing package gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-bluetooth:
 indicator-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
 indicator-bluetooth depends on gnome-bluetooth | ubuntu-system-settings; however:
  Package gnome-bluetooth is not configured yet.
  Package ubuntu-system-settings is not installed.


dpkg: error processing package indicator-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-control-center:
 unity-control-center depends on indicator-bluetooth; however:
  Package indicator-bluetooth is not configured yet.


dpkg: error processing package unity-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-share:
 gnome-user-share depends on gnome-bluetooth; however:
  Package gnome-bluetooth is not configured yet.


dpkg: error processing package gnome-user-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on unity-control-center; however:
  Package unity-control-center is not configured yet.


dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-control-center-signon:
 unity-control-center-signon depends on unity-control-center; however:
  Package unity-control-center is not configured yet.


dpkg: error processing package unity-control-center-signon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of webaccounts-extension-common:
 webaccounts-extension-common depends on unity-control-center-signon | gnome-control-center-signon; however:
  Package unity-control-center-signon is not configured yet.
  Package gnome-control-center-signon is not installed.


dpkg: error processing package webaccounts-extension-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-webaccounts:
 xul-ext-webaccounts depends on webaccounts-extension-common (= 0.5-0ubuntu2); however:
  Package webaccounts-extension-common is not configured yet.


dpkg: error processing package xul-ext-webaccounts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bluez
 bluez-alsa:amd64
 gnome-bluetooth
 indicator-bluetooth
 unity-control-center
 gnome-user-share
 ubuntu-desktop
 unity-control-center-signon
 webaccounts-extension-common
 xul-ext-webaccounts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've used Google to try and find a fix. I've seen posts that show a similar problem and tried to enact the fixes they suggest but none have worked so far or they're for older version of ubuntu.
Entering 'sudo apt-get upgrade' throws me the same error. 

This is one thread that I tried to use to solve the problem, but the line of code that he removed in the mentioned file doesn't exist in the version of ubuntu I'm using.
[http://ubuntuforums.org/showthread.php?t=1912031](http://ubuntuforums.org/showthread.php?t=1912031)

As far as I can work out is that they error due to dependences, but I can't acquire the dependant files because of something that I don't know.

---

### Post by Bucky Ball on 2015-01-16
*Thread moved to **General Help**.*

Welcome. ***Installations & Upgrades*** is for support with installing the Ubuntu OS and its official flavours. ;)

If you installed Ubuntu, you already have ubuntu-desktop installed. Please run:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any and all errors.

---

### Post by will63 on 2015-01-16
Thank you for the fast reply, sorry it was in the wrong section.

Ah I understand, I'll have a look at the different OS's and see which one best fits.
Thanks again for your attention.

---

### Post by Bucky Ball on 2015-01-16
I edited my post, but looks like you read the first version. Yes, installing ubuntu-desktop is the same as installing Ubuntu over the server install. Not much point if you just want the desktop environment. 

This confuses me, though:
```

ubuntu-desktop is already the newest version.
```

Did you install the server version (which has no DE) or Ubuntu? This is indicating Ubuntu. If you want to run the server with a DE, install the server version of Ubuntu then install the Unity DE ONLY, with:

```
sudo apt-get install unity
```

I don't use Unity, but thinking this will do it. Consequently, replace 'unity' in the command above with 'xfce4' for a lighter DE, or lxde for a lighter one again. ;)

---

### Post by will63 on 2015-01-16
I ran the commands given in your edited post and I got 0 errors, this is the first time 'sudo apt-get upgrade' has run without the error.

Ubuntu Server 14.10 "Utopic Unicorn" (64bits) is what I had installed. This is a dedicated server with kimsufi.com so I only have a list of OS's to choose from.

I followed this post after the fresh install: 
[http://askubuntu.com/questions/53822/how-do-you-run-ubuntu-server-with-a-gui](http://askubuntu.com/questions/53822/how-do-you-run-ubuntu-server-with-a-gui)

After running 'sudo apt-get install ubuntu-desktop' for the first time is when I received the error.


'sudo apt-get install unity' ran perfectly and installed.
Now I just need to get remote desktop access to the server sorted. 
Thank you for the help.

---

### Post by Bucky Ball on 2015-01-17
All good. Hope it goes well. Don't hesitate to post a new thread for any further issues. Good luck. ;)

---

### Post by will63 on 2015-01-17
Thank you for your help and for taking the time to reply. 
Really appreciate it :)

---

