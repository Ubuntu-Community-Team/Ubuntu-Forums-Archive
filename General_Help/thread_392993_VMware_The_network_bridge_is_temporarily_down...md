---
title: "VMware: The network bridge is temporarily down.."
date: 2007-03-25
forum: General Help
---

### Post by Fuzzy Logic on 2007-03-25
Hello people!

I recently installed Win2k on VMware Workstation 5.5.3 but I can't really get it working the way I want it.

The first thing I get after powering on the virtual machine is the following message:
> The network bridge on device /dev/vmnet0 is temporarily down because the bridged Ethernet interface is down.  The virtual machine may not be able to communicate with the host or with other machines on your network.

After clicking OK, Win2k starts up but it has only 16 colors and the resolution is 640x480. I guess this is because of the drivers that aren't currently available, but I'm also not able to download any because of the fact that my internet doesn't work.

Does anyone know what I should do? I am using Edgy Eft and I'm not so familiar to Linux, so please explain things the easy way.

Thanks in advance!

---

### Post by jcbwalsh on 2007-03-25
Have you installed the VMWare tools? They add new drivers for better video and mouse control. Go to the Virtual Machine menu and choose Install VMWare Tools. 

For the networking I'd suggest you use NAT instead of Bridged. I've had no problems since I changed that. This can be changed in the individual VM's settings under Ethernet. 

James

---

