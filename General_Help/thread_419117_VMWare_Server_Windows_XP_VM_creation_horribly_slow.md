---
title: "VMWare Server: Windows XP VM creation horribly slow!"
date: 2007-04-22
forum: General Help
---

### Post by incubii on 2007-04-22
Well i've installed Feisty and i like it so far and decided to setup VMWare server now. I was trialing Debian 4.0 when the new Ubuntu was released so i switched over. The only problem i have now is the creation of virtual machines, especially windows, will pause for a good 5 seconds or more, then do about 2 seconds work then pause again! This also happens after everything is completed and its up and running.

I have disabled all snapshotting available on the host and client. It works perfectly fine on vanilla Debian but feisty has issues. 

I am running VMWare server 1.0.2 build-39867, using kernel 2.6.20-15-generic. I applied the vmware-any-any patch to get it working.

Other then that, this is a vanilla feisty.

Any help would be greatly appreciated, but bare in mind i've gone through pretty much all vmware suggestions on this board already to no avail.

Thanks :)

---

### Post by Ziox on 2007-04-22
If you don't mind, give virtualbox a try ([www.virtualbox.com](www.virtualbox.com) and install the edgy version (works for me)).  It is as easy to use as VMWare.  

As for VMware, make sure you install vmware-tools

---

