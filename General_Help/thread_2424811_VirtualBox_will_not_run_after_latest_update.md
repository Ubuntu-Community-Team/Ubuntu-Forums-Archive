---
title: "VirtualBox will not run after latest update"
date: 2019-08-14
forum: General Help
---

### Post by cscj01 on 2019-08-14
I am running Ubuntu 18.04.03 x64 Gnome-flashback, kernel 5.0.0-25-generic, and VirtualBox 6.0.10 r132072 (Qt5.9.5). After the latest software upgrade, I cannot launch any of my VM's. I get the following message:```
RTRinitEX failed with rc=-1912 (rc=-1912)
The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

'/sbin/vboxconfig'

may correct this. Make sure that you are not mixing builds of VirtualBox from different sources.

where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user.
```I ran the following with the results shown:```
sudo /sbin/vboxconfig
[sudo] password for butch: 
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
```What do I need to do to fix this?

---

### Post by SeijiSensei on 2019-08-15
Is this the version of VirtualBox from the Ubuntu repositories?

If so, I recommend using the version in the Oracle repository instead. It's been rock-solid for me across multiple versions of Ubuntu.

Instructions are here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

Installing this version will also install build-essential and dkms so that the VB kernel module is compiled from scratch each time. That ensures it will match the version of the kernel.

---

### Post by cscj01 on 2019-08-15
> **SeijiSensei said:**
> Is this the version of VirtualBox from the Ubuntu repositories?

If so, I recommend using the version in the Oracle repository instead. It's been rock-solid for me across multiple versions of Ubuntu.

Instructions are here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

Installing this version will also install build-essential and dkms so that the VB kernel module is compiled from scratch each time. That ensures it will match the version of the kernel.

It is the version from the Ubuntu repositories.  I think I'll give your suggestion a shot.  I presume I'll need to remove the Ubuntu version before installing from Oracle.  Will this operation allow me to export my VMs from the Ubuntu version and import them into the Oracle version?  If so, I wonder if the current issue will somehow make the exported VMs inoperable (although I can't think of why it would do that).

---

### Post by cruzer001 on 2019-08-15
Yes, first remove vBox and leave the guest files in your home folder.  Guest vm's can become inoperable when doing this, but usually a simple repair is all thats needed.

---

### Post by SeijiSensei on 2019-08-15
I'm pretty sure the Oracle installer removes the Ubuntu version since they have different package names. The Ubuntu version is named just "virtualbox" while the Oracle versions have names like "virtualbox-6.0".  And yes, just leave the VM images where they are, usually in /home/username/Virtualbox VMs/.  If VB doesn't find them automatically, you can reimport them using the Machine > Add entry in the main menu.

If you want extra protection, you can use File > Export Appliance in your current installation to create a portable version of each VM, then use File > Import Appliance in the new version of VirtualBox.

---

### Post by cscj01 on 2019-08-20
All is well.  Thanks for the help.

---

