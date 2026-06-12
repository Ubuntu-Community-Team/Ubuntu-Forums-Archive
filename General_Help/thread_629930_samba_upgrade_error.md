---
title: "samba upgrade error"
date: 2007-12-02
forum: General Help
---

### Post by wmoon on 2007-12-02
Please help me deal with the following error.





wmoon@wmoon-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba samba-common
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba-common
The following packages will be upgraded:
  samba
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4928kB of archives.
After unpacking 5022kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: unable to initialize frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 148308 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.3 (using .../samba_3.0.22-1ubuntu3.5_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Selecting previously deselected package samba-common.
Unpacking samba-common (from .../samba-common_3.0.22-1ubuntu3.5_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

