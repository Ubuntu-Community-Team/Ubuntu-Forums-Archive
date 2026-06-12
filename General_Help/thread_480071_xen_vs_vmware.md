---
title: "xen vs vmware"
date: 2007-06-21
forum: General Help
---

### Post by maddot on 2007-06-21
Browsing on the internet, i spotted that suse has adopted an experimental vrtualisation, xen. Currently, i believe ubuntu supports vmware, from m$ to linux and linux to m$. But has anyone tried Xen and knows any particular destinction between the two? or...are they just another clone with a diffrent name :X

Edit:
Well, after continuous digging up... apparently xen is supposed to be faster than vmware and it is open source. So why isn't ubuntu pushing for it to be iit's primary contender?

---

### Post by zero-9376 on 2007-06-21
pretty sure that xen requires a different kernel and may not yet have the admin tools that make vmware and virtual box so easy to use.

---

### Post by incubus on 2007-06-21
maddot,

The story is a bit complicated, with its share of overhype.  Xen is a very good and seriously developed product, but unfortunately its requirement of a modified Kernel always kept a lot of users away from it.  It is being used by companies out there -- I know of hosting companies that will give you a virtual machine like this.

For most users who just want to run Windows in a point-and-click way, VMware has been more attractive.  It looks like VirtualBox is another serious contender in this arena.  

Among these alternatives (I'm of course omitting a lot of other options), KVM was kind of chosen as the way to go with virtualization for Linux, in the sense that it was to be included as a Kernel module.  And indeed it is now, you can check the repositories.  KVM basically uses QEMU as its front-end, which I personally like.  QEMU is a program for hardware emulation that has been around for a while.  To be fast it had its own solution: KQEMU.

The thing with KVM and Xen is that you need a processor with VT (virtualization technology) to really enjoy the speed gains.  VMware has been arguing that their technology is almost equivalent and you don't actually need VT.

So OK, to wrap it up, I think Ubuntu and other distros are pushing more for KVM now.  However, in practice I notice that many people have been using VMware and VirtualBox.  It has to do with ease of use (i.e., nice GUIs) and also with the fact that KVM's development is still shaping up.  It was working well for me, though.

incubus

---

### Post by ealaqqad on 2007-10-17
Hi,

It seems for Xen to perform well it has to change in the Linux Kernal. That explain why Xen does not perform quite well with windows, as still no way to change the kernal of windows. Xen will perform better with windows 2008 as it will has a built in hypervisor. though for a complete comparison between Xen & VMware please look at fully detailed comparison at [www.itcomparison.com](www.itcomparison.com).

Enjoy :guitar:
IBMer007

---

### Post by LanDan on 2007-10-17
both are seperate technologies indeed, but both need a modified kernel,

if you want to play around i would recomend the free vmware product or virtualbox
if you want a production environment i would recommend xen or the paid vmware product

---

