---
title: "vmware server problem - error during install"
date: 2007-09-05
forum: General Help
---

### Post by noworry on 2007-09-05
Hi,
   When I try to install vmware server from the repository using apt-get, I am getting an error as shown below. It exits even before asking for serial number.

$sudo apt-get install vmware-server vmware-tools-kernel-modules
...
Setting up vmware-server (1.0.3-1) ...
/etc/init.d/vmware-server: 176: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.
invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Setting up vmware-tools-kernel-modules-2.6.20-16 (2.6.20.5-16.29) ...
Setting up vmware-tools-kernel-modules (2.6.20.16.28.1) ...
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

Actually no directory by name /etc/vmware exists. 
I tried removing the packages and installing again, but still getting the same error.

Please help me out in this.

Thanks in advance,
noworry

---

### Post by ronnieredd on 2007-09-05
Which version of Ubuntu are you using?
If you are using 7.04, there's now a repository for VMware server.
First try vmware-uninstall.pl in case some of it got installed. Then try these instructions:
**[HowTo install vmware server via canonical repository.]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")**

---

### Post by noworry on 2007-09-06
I have Ubuntu Feisty 7.04 and I tried the same link that you have given. BTW, there is no vmware-uninstall.pl anyware in my system. Don't know what is the problem :confused:

---

### Post by caseface on 2007-09-07
> **ronnieredd said:**
> Which version of Ubuntu are you using?
If you are using 7.04, there's now a repository for VMware server.
First try vmware-uninstall.pl in case some of it got installed. Then try these instructions:
**[HowTo install vmware server via canonical repository.]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")**

Sorry for being such a noob, but can you give the command to paste into terminal?
The other command line, for when it was partially installed using synaptic would be helpful also.

---

### Post by noworry on 2007-09-11
I got it working by installing vmware server 1.0.2 on my machine (looks like some problem between 1.0.3 and my ubuntu install). 
I followed the tutorial [http://ubuntuforums.org/showpost.php?p=2384779&postcount=52](http://ubuntuforums.org/showpost.php?p=2384779&postcount=52) for installing vmware and I followed [http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/) for the rest of the settings and configuration.
It is now working like a charm and I am very very happy :)

---

