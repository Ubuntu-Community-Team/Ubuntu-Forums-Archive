---
title: "Problem when try to remove automatix"
date: 2007-04-19
forum: General Help
---

### Post by Th1eF` on 2007-04-19
i try to remove automatix and i get the following error
> 
:~$ sudo apt-get remove automatix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package automatix is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python2.5-minimal libxdamage-dev libqt3-headers libgl1-mesa-dev python2.5
  x11proto-gl-dev mesa-common-dev x11proto-damage-dev libxcomposite-dev
  x11proto-composite-dev ktuberling libstartup-notification0-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gtk-engines-eazel (0.3-5.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing gtk-engines-eazel (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gtk-engines-eazel
E: Sub-process /usr/bin/dpkg returned an error code (1)

any idea to fix it?

---

