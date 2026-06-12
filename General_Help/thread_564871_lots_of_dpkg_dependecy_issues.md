---
title: "lots of dpkg dependecy issues?"
date: 2007-10-01
forum: General Help
---

### Post by ScottKidder on 2007-10-01
scott@scottdesk:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxrender-dev mesa-common-dev
  linux-libc-dev libstartup-notification0-dev x11proto-composite-dev
  libxcursor-dev x11proto-randr-dev x11proto-damage-dev libxdamage-dev
  x11proto-fixes-dev libxcomposite-dev libxrandr-dev libmeanwhile1
  libxfixes-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up kdebase-bin (3.5.7-0ubuntu1~feisty2) ...
/var/lib/dpkg/info/kdebase-bin.postinst: 16: gtk-update-icon-cache: Input/output error
dpkg: error processing kdebase-bin (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdesktop:
 kdesktop depends on kdebase-bin (= 4:3.5.7-0ubuntu1~feisty2); however:
  Package kdebase-bin is not configured yet.
dpkg: error processing kdesktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-kio-plugins:
 kdebase-kio-plugins depends on kdesktop; however:
  Package kdesktop is not configured yet.
dpkg: error processing kdebase-kio-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on kdebase-kio-plugins; however:
  Package kdebase-kio-plugins is not configured yet.
dpkg: error processing amarok (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amarok-xine:
 amarok-xine depends on amarok (= 2:1.4.7-0ubuntu1~feisty1); however:
  Package amarok is not configured yet.
 amarok-xine depends on amarok; however:
  Package amarok is not configured yet.
dpkg: error processing amarok-xine (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdebase-bin
 kdesktop
 kdebase-kio-plugins
 amarok
 amarok-xine



It's been doing this for all kinds of apps including pidgin, and the new version of Open Office. I had Amarok previously installed and then kdebase-bin was doing this same thing, so I uninstalled and now reinstalling I get these errors again

---

### Post by brownknight on 2007-10-01
Hi. Have you tried 

sudo aptitude install -f  

(aptitude is better than apt-get)

---

### Post by strabes on 2007-10-01
I don't know if this will work but one thing you could try is to overwrite your existing sources.list with the sources from [here](http://www.psychocats.net/ubuntu/sources#feisty).

Then run:```
sudo aptitude update && sudo aptitude upgrade
```

---

