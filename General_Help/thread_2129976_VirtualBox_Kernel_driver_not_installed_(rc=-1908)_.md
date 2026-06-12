---
title: "VirtualBox Kernel driver not installed (rc=-1908) Ubutnu 12.10"
date: 2013-03-27
forum: General Help
---

### Post by Fredhoud on 2013-03-27
I have a new  HP2000 laptop, and I installed VirtualBox with Windows XP with no problem at all.  A week ago later, I replaced the hard drive with a Kingston Solid State hard drive.  I installed VirtualBox, but I can't get it to work.
I have installed gDebi, Synaptic, and dkms package.  Also have acivated users and groups, and checked the permission for VirtualBox.  The funny thing is that I didn't have any issue before with the original regular-standard hard drive.  I don't know if a solid state dirve has anything to do with it? The following the actual error that I get when I try to start the machine to install the Windowd XP cd. 

Failed to open a session for the virtual machine XP-VB.
The virtual machine 'XP-VB' has terminated unexpectedly during startup with exit code 1.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}
=======================
Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing
'/etc/init.d/vboxdrv setup'
as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I am totally stuck, and would appreciate any suggestion or idea to fix this?  Also, please keep in mind that I am new to Linux, and have a very limited knowledge.  So please keep it as simple as possiblle.

FredHoud

---

### Post by Vaphell on 2013-03-27
i experience similar things from time to time, i think it happens after kernel upgrade
i simply run
```
sudo apt-get remove virtualbox-4.2   
sudo apt-get install virtualbox-4.2
```
to fix it (oracle version here)

---

### Post by Fredhoud on 2013-03-28
I downloaded VirtualBox from Oralce  [virtualbox-4.2_4.2.10-84104~Ubuntu~quantal_amd64.deb]("http://download.virtualbox.org/virtualbox/4.2.10/virtualbox-4.2_4.2.10-84104%7EUbuntu%7Equantal_amd64.deb")
It says " Package 'virtualbox-4.2' has no inltallation candidate. 
Last night I tried to install it with GDebi package installer, and evedinlty had a conflict and installed the 4.2.18.  I then tried to install it through software center and got the following error:
Breaks existing package 'virtualbox'. But the '/home/fred/Download/virtualbox-4.2-4.2.10-84104~Ubuntu~precice_amd64.deb' provides it via: virtutal box'.
I have a 64 bit operating system, and that's the only package listed for Ubuntu 12.10.  Any other suggestion?

---

### Post by Vaphell on 2013-03-28
set up PPA for virtualbox like a civilized man and let your system figure things out
[http://www.ubuntuupdates.org/ppa/virtualbox.org_contrib](http://www.ubuntuupdates.org/ppa/virtualbox.org_contrib)

```
sudo apt-get update
apt-cache search virtualbox
```
if you get virtualbox-4.2 in results
```
sudo apt-get install virtualbox-4.2
```

---

