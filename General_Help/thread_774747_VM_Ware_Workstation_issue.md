---
title: "VM Ware Workstation issue"
date: 2008-04-29
forum: General Help
---

### Post by sniffcrisps on 2008-04-29
Hi,  I've just upgraded from 7.10 to 8.4 and (apart from some problems with my soundcard) it all went OK.  The problem is that every time I upgrade to the latest release of Ubuntu, it stops my VM Ware Workstation from working.  Why is this?

---

### Post by rbmorse on 2008-04-29
VMWorkstation needs to be configured for the specific kernel version in use by the O/S. When you upgrade Ubuntu you normally install a different kernel version, so you have to run the VMWare installer again to configure it for the kernel now in use. 

ATI and nVidia video drivers need to reinstalled for the same reason.

---

### Post by ghost_ryder35 on 2008-04-29
> **sniffcrisps said:**
> Hi,  I've just upgraded from 7.10 to 8.4 and (apart from some problems with my soundcard) it all went OK.  The problem is that every time I upgrade to the latest release of Ubuntu, it stops my VM Ware Workstation from working.  Why is this?
check out the virtualization forum here.  this has been discussed a lot.  You have to download some fixes for some files to so they will compile correctly on the new kernel

the easiest verson of vmware workstation to get working on the new kernel is 6.5 beta
see 
[http://blog.zmang.com/installing-vmware-workstation-65-beta-on-ubuntu-hardy-heron-804-faqs/](http://blog.zmang.com/installing-vmware-workstation-65-beta-on-ubuntu-hardy-heron-804-faqs/)

---

### Post by sniffcrisps on 2008-04-29
> **ghost_ryder35 said:**
> check out the virtualization forum here.  this has been discussed a lot.  You have to download some fixes for some files to so they will compile correctly on the new kernel


Yes, but the problem I have here (using Dell Inspiron 1525 laptop) is that the default kernel is the i386 which, when I try to reinstall VM Ware tells me cannot be found!

---

