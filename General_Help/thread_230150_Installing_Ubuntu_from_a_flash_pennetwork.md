---
title: "Installing Ubuntu from a flash pen/network"
date: 2006-08-05
forum: General Help
---

### Post by xenomorph99 on 2006-08-05
Hi,

Is it possible to install Ubuntu (or any Linux for that matter) from either the network or a flash pen without booting from them?

I have an old laptop which doesn't have a floppy or CD but it does have a USB port (which I cannot boot from, unfortunately). What I'd like to do is to somehow copy the files over to it (it has Windows 2k on it at the moment) either via a flashpen or the USB<->Network adaptor. I imagine I need to somehow:

a. Copy the distro files over to the target machine, perhaps on a FAT32 partition.
b. Get a partition manager to run so I can at least set up a / and swap partition in addition to the FAT32 partition.
c. Copy the files..and set it up...and set up GRUB.

Is there a simple way of doing this or is it just easier to retain W2K?

Ta,
Xeno

---

### Post by noof on 2006-08-07
Can you boot your lappy from the network? I did something like this: 
* [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
* [http://halisway.blogspot.com/2006/06/ubuntu-dapper-pxe-network-install.html](http://halisway.blogspot.com/2006/06/ubuntu-dapper-pxe-network-install.html) 
to install breezy on my lappy, worked like a charm. But if you only have a USB network adapter I doubt you can boot from it.

---

