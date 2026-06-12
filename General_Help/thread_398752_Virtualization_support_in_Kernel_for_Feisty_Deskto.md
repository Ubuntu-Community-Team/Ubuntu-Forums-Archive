---
title: "Virtualization support in Kernel for Feisty Desktop too?"
date: 2007-04-01
forum: General Help
---

### Post by darkmaster on 2007-04-01
Hi, on the Feisty Beta announcement, there's this notification:

> Desktop highlights

Windows migration tool: The new migration tool recognises Internet Explorer bookmarks, Firefox favourites, desktop wallpaper, AOL IM contacts, and Yahoo IM contacts, and imports them into Ubuntu during installation. This offers easier and faster migration for new users of Ubuntu and individuals wanting to run a dual-boot system.

Easy-to-install codec wizards: A new guided wizard for installing codecs not shipped with Ubuntu gives users a safe way of installing codecs they can legally use to view multimedia content.

Plug and play network sharing with Avahi: This new feature allows users to automatically discover and join a wireless network and share music, find printers and more.
Server highlights

Virtualisation support: On x86 systems with the Intel VT or AMD-V extensions, Kernel-based Virtual Machine support (KVM) allows users to run multiple virtual machines running unmodified Linux. Each virtual machine has private virtualised hardware: a network card, disk, graphics adapter, and so on. We have also added VMI support, which provides optimised performance under VMWare.

I was wondering if the Kernel Virtualization would be available in the desktop version of feisty too. Why should the server verson use a different kernel? I allready heard about this new virtualization in kernel feature that Linus himself inserted into the newest Linux Kernel. So, is it going to be featured in Desktop Ubuntu too? And if not, how will we be able to add this functionality to the desktop version of Feasty we install?

---

### Post by jmillikin on 2007-04-02
KVM's not as much a highlight for desktop systems as it is for servers. But yes, you will be able to use it on a normal desktop. Just apt-get install kvm.

---

### Post by darkmaster on 2007-04-03
> **jmillikin said:**
> KVM's not as much a highlight for desktop systems as it is for servers. But yes, you will be able to use it on a normal desktop. Just apt-get install kvm.

Oh, very well, I'm very happy about it! Somebody sayd that a virtual machine virtualized in KVM can virtualize also the 3D Video Card instead of emulating a 2D card. But I guess this is science fiction, right? I don't think it is possible. It would be a total revolution for virtualization. They sayd it was possible because the machine is virtualized directly inside the Kernel, so... but it is absurd. Right?

---

