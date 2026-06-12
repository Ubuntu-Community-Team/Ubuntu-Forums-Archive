---
title: "Install using PCI LAN"
date: 2015-11-24
forum: General Help
---

### Post by Jan_Erik on 2015-11-24
I have a number of T61 and no CD player in boot sequence. I also do not have the supervisor password. However the PCI LAN is in the boot sequence. Is it straight forward to install Ubuntu using this option or is it complicated to setup? I can get the supervisor to change the boot sequence but I am just checking if it might be just as easy to install using the LAN?

---

### Post by sandyd on 2015-11-24
You will need to a setup PXE server on the LAN to do a network boot.

See [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer) for details on how to set up one on Ubuntu (Note - requires seperate machine)

---

### Post by matt_symes on 2015-11-24
Hi

> **Jan_Erik said:**
> I have a number of T61 and no CD player in boot sequence. I also do not have the supervisor password. However the PCI LAN is in the boot sequence. Is it straight forward to install Ubuntu using this option or is it complicated to setup? I can get the supervisor to change the boot sequence but I am just checking if it might be just as easy to install using the LAN?

I've got this in my LAN and use it for testing ISO and also to fix computer.

To do it i installed...

A dhcp server (isc-dhcp-server). My router at the time could not be configured as to the location of pxelinux.0 and the other boot files.

A tftp server and inetd. Obviously to give out the bootmenu and pxelinux.0 files.

A NFS server to serve the root filing system as i didn't want to use apache to do that.

The iso images theselves can be bind mounted so they don't need to be extracted. Just the bootmenu needs to be configured correctly to point to the kernel and initrd and the kernel boot parameters to point to the nfs exported, bind mounted iso.

I looked into preseeding briefly but never followed it up.

Does what i need and works a treat.

I have set up a cron job that is currently zsyncing the daily ISOs  at 4am and automatically mounting and unmounting them as required when zsynced so it's very simple to install them.

I use it to install new ISO's play with the dailies and, what i originally set it to for, to be able to boot into PXE enabled but otherwise broken PCs to attempt to fix then from live environment; both Linux and not.

It may or may not be overkill for your need but does not take too long to set up once you have done it.

Kind regards

---

