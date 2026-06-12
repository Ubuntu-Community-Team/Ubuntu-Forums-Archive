---
title: "Cant install htop, apache and openssh, basically anything"
date: 2016-01-11
forum: General Help
---

### Post by jakr2 on 2016-01-11
I cant install nothing on my machine as I get these errors below for mostly everything. I've looked up many fix's for the problem, tried all that I've found and none have worked.

Trying to install htop
```
root@ctrl:/# apt-get install htopReading package lists... Done
Building dependency tree       
Reading state information... Done
htop is already the newest version.
The following packages were automatically installed and are no longer required:
  attr avahi-utils libaio1 libhdb9-heimdal libkdc2-heimdal python-cupshelpers
  python-dnspython python-gnomekeyring python-libxml2 samba-dsdb-modules
  samba-vfs-modules system-config-printer-udev tdb-tools
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/488 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package samba-common-bin (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Trying to install openssh
```
root@ctrl:/# apt-get install openssh-serverReading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
The following packages were automatically installed and are no longer required:
  attr avahi-utils libaio1 libhdb9-heimdal libkdc2-heimdal python-cupshelpers
  python-dnspython python-gnomekeyring python-libxml2 samba-dsdb-modules
  samba-vfs-modules system-config-printer-udev tdb-tools
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/488 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package samba-common-bin (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Trying to install apache
```
Errors were encountered while processing: samba-common-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by SeijiSensei on 2016-01-11
Run "sudo dpkg --configure -a" and see if that solves the problem.  If not, remove samba-common-bin with "sudo apt-get remove --purge samba-common-bin" then reinstall it.

---

### Post by jakr2 on 2016-01-11
> **SeijiSensei said:**
> Run "sudo dpkg --configure -a" and see if that solves the problem.  If not, remove samba-common-bin with "sudo apt-get remove --purge samba-common-bin" then reinstall it.
That didnt solve the problem. But soon after I posted this I found a fix.
```
 dpkg --remove --force-remove-reinstreq samba-common-bin 
```
```
 apt-get autoremove 
```
```
 apt-get install htop 
```
Works fine now

---

### Post by ian-weisser on 2016-01-11
> **jakr2 said:**
> dpkg --remove --force-remove-reinstreq samba-common-bin 

Obligatory disclaimer for future readers:
dpkg commands are risky. Used improperly, dpkg will happily destroy your system.
Any dpkg --force command should not be the first (or second or third) choice to fix a packaging problem. Best practice is to save the nuclear option for last; try several less-risky approached first.

If uninstalling software, that command won't actually remove it. It will simply lie to the package manager database, claiming that the files have been deleted. You must still clean up the leftover files (manually) to prevent several possible headaches in the future.

---

