---
title: "VMware question"
date: 2006-10-10
forum: General Help
---

### Post by Naegling23 on 2006-10-10
Right now I am dual booting kubuntu and windowsxp.  Is there a way to install a vmware player type thinger without installing windows?  One that will use my existing windows install?

I installed vmware player through automatix, will this program do the trick?

---

### Post by Jeremy23 on 2006-10-10
I tried booting my existing Windows partition with VMware and all it did was blue-screened. I *don't* recommend booting existing Windows partitions with VMware due to hardware issues you will probably encounter.

You can, of course, boot a freshly installed Windows XP off a VMware image. See [EasyVMX]("http://www.easyvmx.com/") for creating VMX (virtual machine) files.

---

### Post by jpkotta on 2006-10-10
> **Naegling23 said:**
> Right now I am dual booting kubuntu and windowsxp.  Is there a way to install a vmware player type thinger without installing windows?  One that will use my existing windows install?

I installed vmware player through automatix, will this program do the trick?

Think of VMWare as a virtual computer.  How would you "install" Windows on a new computer and have it use your existing installation on an old computer?  You have to physically move the hard drive and then the installation on the old one doesn't exist (and then there's product activation...).  As far as I know, this is exactly how VMware works, and you can't run an existing physical installation in the virtual machine.  But if you use VMware Server, you can install Windows, and you can copy all of your data into the virtual machine (or better yet, in a shared partition).

[https://help.ubuntu.com/community/VmwareServer](https://help.ubuntu.com/community/VmwareServer)

---

