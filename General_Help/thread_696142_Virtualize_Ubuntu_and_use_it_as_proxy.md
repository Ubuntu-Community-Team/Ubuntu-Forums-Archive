---
title: "Virtualize Ubuntu and use it as proxy?"
date: 2008-02-13
forum: General Help
---

### Post by Fredericks on 2008-02-13
I was curious if there's a way to establish an internet connection through a virtualized copy of Ubuntu running inside XP? I'm attempting to use the virtualized copy as a proxy.

---

### Post by Quadratic on 2008-02-13
You can install Ubuntu within VMWare or VirtualPC (easier with VMWare), and give it it's own MAC and IP addresses to be used over the network. In VMWare, set up "Bridged" networking in the virtual machine settings to do this. Your host computer can also talk to the Linux virtual machine just like a real one.

---

### Post by Fredericks on 2008-02-13
Thanks, will give this a shot.

---

### Post by Fredericks on 2008-02-15
Well, took me a bit to get everything set up. Had some school related issues that took priority.

Anyways, I attempted to the setup, have a copy of Ubuntu running in VMware Server under XP. But I think I mis-stated my objective earlier. In VMware terms, I'm attempting to have the host, Windows, connect to the internet through the client, Ubuntu. Basically I'm trying to make it seem as if I'm running Ubuntu when I'm running XP. Is this still the best way to go about this, or is there a better way?

I need to be able to work under a Windows environment, since some programs I've been working on are currently only being designed for Windows. Due to some complications however, I cannot get online using a Windows machine without enabling software that causes problems with the programs I'm writing. Any other OS is permitted internet access without the software. If I didn't need full 3D support for the programs, I'd simply virtualize XP in Ubuntu and the problem would be solved. So that leaves me where I am now, trying to make it appear that I'm using Ubuntu when I'm really using XP. I'm not well versed in most topics network related, so I apologize if this isn't explained terribly well. Any help would be greatly appreciated.

-Fredericks

---

### Post by theRightNee on 2008-04-03
just used a bridged networking, and give each OS its own IP

then do not connect to the internet through the Windows OS, and only through the Ubuntu one.
this should solve your issues...and if it is a wireless connection, you may have some problems with getting the device to work..but that is for another time...

o and then you will want to set up Samba so that you can transfer data from the Ubuntu OS to the Windows host, because it seems that is going to show up..just google and you'll find it

---

