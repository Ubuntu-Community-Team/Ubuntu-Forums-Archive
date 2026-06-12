---
title: "Errors were encountered while processing:  linux-cloud-tools-common"
date: 2015-02-26
forum: General Help
---

### Post by phill2 on 2015-02-26
I'm running a Ubuntu 14.04 server on the Azure network.

Recently, I frequently see the same error when upgrade &/or installing packages;

```
Errors were encountered while processing:
 linux-cloud-tools-common
```

If I run ```
**sudo apt-get -f install**
```
it gives the following output:

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-cloud-tools-common (3.13.0-46.75) ...
start: Job failed to start
invoke-rc.d: initscript hv-kvp-daemon, action "start" failed.
dpkg: error processing package linux-cloud-tools-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-cloud-tools-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


If I try ```
**dpkg --configure -a**
``` I get the following response:

Setting up linux-cloud-tools-common (3.13.0-46.75) ...
start: Job failed to start
invoke-rc.d: initscript hv-kvp-daemon, action "start" failed.
dpkg: error processing package linux-cloud-tools-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-cloud-tools-common



Also if I try ```
**sudo dpkg -C**
```it responds with:

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-cloud-tools-common Linux kernel version specific cloud tools for version

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 libjson0:amd64       JSON manipulation library (transitional package)



I'm fairly newb to Ubuntu & Linux, so any help would be greatly appreciated.

Thanks in advance

---

