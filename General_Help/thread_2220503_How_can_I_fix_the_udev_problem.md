---
title: "How can I fix the udev problem?"
date: 2014-04-28
forum: General Help
---

### Post by honglianglu87 on 2014-04-28
Thank adevance, please help me out! 
I upgrade from 13.10 to 14.04, but there is problems occured, so I rescued through KNOPPIX livecd. Just now the problem is:
when i tried to :
```
dpkg --configure -a
```
The result is:
```
Setting up whoopsie (0.2.24.5) ...
invoke-rc.d: unknown initscript, /etc/init.d/whoopsie not found.
dpkg: error processing package whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 100
Setting up lirc (0.9.0-0ubuntu5) ...
 * udev requires devtmpfs support, not started
   ...fail!
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing package lirc (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up udev (204-5ubuntu20) ...
 * udev requires devtmpfs support, not started
   ...fail!
invoke-rc.d: initscript udev, action "restart" failed.
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on udev; however:
  Package udev is not configured yet.


```
and the apt-get upgrade and dist-upgrade get same result!

---

