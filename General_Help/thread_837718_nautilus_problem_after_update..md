---
title: "nautilus problem after update."
date: 2008-06-22
forum: General Help
---

### Post by ultimatsz on 2008-06-22
my laptop works fine but using synaptic now gives this error

E: desktop-file-utils: subprocess post-installation script returned error exit status 2
E: nautilus: dependency problems - leaving unconfigured


what can i do?

---

### Post by iaculallad on 2008-06-22
Try to re-install your desktop-file-utils:

```
sudo apt-get --reinstall install desktop-file-utils
```

---

### Post by ultimatsz on 2008-06-22
```
ultimatsz@ultima-ubuntu:~$ sudo apt-get --reinstall install desktop-file-utils
[sudo] password for ultimatsz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libglitz-glx1 libgtk1.2 libglitz1 libavifile-0.7c2
  libgtk1.2-common libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up desktop-file-utils (0.15-1ubuntu4) ...
dpkg (subprocess): unable to execute post-installation script: Input/output error
dpkg: error processing desktop-file-utils (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on desktop-file-utils (>= 0.7); however:
  Package desktop-file-utils is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 desktop-file-utils
 nautilus
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

error in detail. tried to reinstall desktop-file-utils dpkg apt and nautilus.

---

### Post by iaculallad on 2008-06-22
Try to:

```
sudo apt-get install --fix-missing
```

---

### Post by ultimatsz on 2008-06-23
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up desktop-file-utils (0.15-1ubuntu4) ...
dpkg (subprocess): unable to execute post-installation script: Input/output error
dpkg: error processing desktop-file-utils (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on desktop-file-utils (>= 0.7); however:
  Package desktop-file-utils is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 desktop-file-utils
 nautilus
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

same thing. any help? thanks

edit: after typing --fix-missing

---

### Post by ultimatsz on 2008-06-23
```
ultimatsz@ultima-ubuntu:~$ sudo apt-get install dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg is already the newest version.
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libglitz-glx1 libgtk1.2 libglitz1 libavifile-0.7c2
  libgtk1.2-common libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 191 package `kino':
 `Depends' field, invalid package name `libgrchitecture:': character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
ultimatsz@ultima-ubuntu:~$ 

```

after upgrading to 2.6.24-19 with some other upgrades like compiz. it became like this..

---

