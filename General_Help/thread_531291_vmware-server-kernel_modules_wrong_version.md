---
title: "vmware-server-kernel modules wrong version"
date: 2007-08-21
forum: General Help
---

### Post by abracadaver on 2007-08-21
Kubuntu (Feisty) -- I've seen many how-tos on installing vmware-server and it seems that it should be very straight forward using apt-get, however I see the following problems:

1. the vmware-server-kernel-modules should install the correct modules for my kernel, unfortunately my kernel is 2.6.20-16!

$uname -a
Linux private 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

$sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  netkit-inetd vmware-server-kernel-modules vmware-server-kernel-modules-2.6.20-15
The following NEW packages will be installed:
  netkit-inetd vmware-server vmware-server-kernel-modules vmware-server-kernel-modules-2.6.20-15
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/82.3MB of archives.
After unpacking 138MB of additional disk space will be used.
Do you want to continue [Y/n]?

2. After this, I can't install vmware-server-kernel-modules-2.6.20-16, it fails and I of course can't uninstall vmware-server-kernel-modules-2.6.20-15.

Any help?

Thanks!
-Shawn

---

### Post by RudolfMDLT on 2007-08-21
I would just download VMware from their website and let the thing compile from source. It's actually really easy.

Anyway - just went to synaptic and found the -16 kernel modules.

Try this:

sudo apt-get update

then 

sudo apt-get install vmware-server

or just go to synaptic and install it with the mouse! :)

cheers,

Rudolf

PS: when I do "sudo apt-get install vmware-server" it says package not found? are you using a non Ubunutu repo?

---

### Post by abracadaver on 2007-08-21
Yes, I have downloaded and built from vmware, however there is a patch that's needed and I was hoping to have it easily upgradeable from apt when there is a newer one and also when I upgrade my kernel.

As for apt-get vmware-server, yes that's what I tried, it depends on vmware-server-kernel-modules which always installs the 2.6.20-15 instead of the 2.6.20-16 that I see is available.

vmware server seems to come from here:  archive.canonical.com_ubuntu_dists_feisty-commercial_main_binary-i386_Packages

-Shawn

---

### Post by RudolfMDLT on 2007-08-21
O! - so are you gonna try the -16 kernel modules manually?

Does the Vmware in the repo allow the creation of Virtual Machines or is it just a player?

---

### Post by abracadaver on 2007-08-21
Both are available as well as some tools and different versions of kernel modules for the server or player.

vmware-server - Free virtual machine server from VMware
vmware-player - Free virtual machine player from VMware

I'm hesitant to try the -16 modules manually because my reason for wanting to use the apt deb packages was so that I could use the vmware-server-kernel-modules  (vmware-server kernel module dependency package) to keep the modules updated with my kernel.

The way I have it now I just run vmware-config.pl to rebuild for a new kernel so the same as manually updating a package and hoping that there is a new one for the new kernel.

Thanks!
-Shawn

---

