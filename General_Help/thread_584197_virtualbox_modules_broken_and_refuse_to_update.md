---
title: "virtualbox modules broken and refuse to update"
date: 2007-10-20
forum: General Help
---

### Post by Alpha_Cluster on 2007-10-20
I've had this problem for awhile but now I actually need to use Virtual Box and would like to see the update icon go away so does anyone know how to fix this problem? Btw this is with gutsy.

```
[@Sakura:~]$ sudo apt-get remove virtualbox-ose-modules-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  module-assistant kbuild libxalan110 libxerces27
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-ose-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 913kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 146776 files and directories currently installed.)
Removing virtualbox-ose-modules-2.6.22-14-generic ...
 * Stopping VirtualBox kernel module vboxdrv                                    invoke-rc.d: initscript vboxdrv, action "stop" failed.
dpkg: error processing virtualbox-ose-modules-2.6.22-14-generic (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 virtualbox-ose-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How do i fix this so i can upgrade?

---

