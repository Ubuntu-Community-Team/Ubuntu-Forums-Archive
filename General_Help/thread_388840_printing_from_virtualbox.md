---
title: "printing from virtualbox"
date: 2007-03-20
forum: General Help
---

### Post by scotttkd on 2007-03-20
have been searching far and wide and can not find any reference as to whether this is even supported by virtualbox.  I need to be able to print to a network printer from a virtualbox winxp vm.  I am connected to the printer via samba on my edgy  based laptop.  printer works fine in edgy, but I have no idea how to make virtualbox see it.  vm sees my usb drive, cdrom, etc. so I know it is installed and working properly.  Any help would be much appreciated.

thanks in advance

scott

---

### Post by scxtt on 2007-03-20
is the XP VM running on the edgy-based laptop?  can't you just use samba w/in the XP VM to connect to the printer?  does the VM have an IP on the same network?

---

### Post by scotttkd on 2007-03-20
hi...thanks for the reply.  VM is WInXP and is running on edgy on a laptop.  edgy is getting dhcp from a linksys wireless router with a 192.168........  ip range, wireless works fine.   vm has a 10.0.27......range that appears to be assigned by the virtualbox, also internet working fine.   I have not had any success in getting the virtualbox to see either the laptop shared printers, or the home office network I have set up.  vm only sees itself.  I assume this is due to the difference in ip addresses but am not clear on how to change.  If I modify the vm ip address to the range the rest of my computers are working on I lose it loses internet connectivity.  tried a direct connected printer on the edgy laptop and still can not be seen in virtualbox.  I know I must be missing something basic, but I can't seem to stumble into it.

scott

---

### Post by scxtt on 2007-03-20
well, i've not used virtualbox, but VMware allows me to assign an IP on my PHYSICAL network (192.168.1.1) by using a bridged connection - so it's not routed through some virtual network interface on the host ... basically i can bring up an interface on the VM w/ an IP that's part of my host's/router's network:

ROUTER: 192.168.1.1
HOST: 192.168.1.100
VM1: 192.168.1.101
VM2: 192.168.1.102
VM3: 192.168.1.103
etc. ...

i'd try to get that working 1st and foremost ...

---

### Post by scotttkd on 2007-03-22
yeah...I have since found out the bridged network rather than NAT is the trick.  I have set up a new vm and all working as planned.  Thanks for the assist!!

scott

---

### Post by ronald_stall on 2007-04-28
Scotttkd just how did you get set up to print in Virtualbox. Same issue here, cannot figure it out. Help is appreciated.

---

### Post by zdude on 2007-04-28
I setup a bridge network so the vbox-VM uses the same IP address space (i.e. 192.168.0.x). I am currently using a samba share for my printer (for my other window boxes) so it was trivial to connect my winxp VM  to my ubuntu samba share. There  are various threads on using bridging via tun/tap interfaces in ubuntu.

---

### Post by chem_prof2000 on 2008-03-29
I have been using VirtualBox for several months but cannot print in ANY of the 4 Linux installations that I can run through it: Edubuntu, Ubuntu, Mandriva 2008, and Fedora 8 (one at a time, of course). I am running VirtualBox on a WIndows XP Toshiba Satellite with 1.5 Gig of RAM.  The Toshiba's wireless G works fine with VirtualBox and I can access the Internet in all 4 distros.  All 4 are updated.  I have followed all the instructions in the docoumentation, but get no printing.

---

