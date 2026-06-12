---
title: "Trying to setup a custom system with Remastersys"
date: 2015-08-03
forum: General Help
---

### Post by marthamarhta on 2015-08-03
I have just successfully set up KVM passthrough with my GTX 750TI.
I patched the 3.18.0 Kernel with ACS / i915 and followed this guide:[https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768).
The Virtual Machine uses Windows 10 and works flawlessly.
Now  I wanted to take it one step further and use remastersys, in order to  create a Live CD of that system, to be able to run such gpu passed  Virtual Machines from a Live CD. 
After creating and booting the LiveCD, I get the following error when I run the script, that initiates the virtual machine:


```
 vfio: error no iommu_group for device
```

I have realized, that remastersys does not include the grub.cfg in /boot/grub/grub.cfg , since it uses isolinux as a bootloader.
This could be the reason for the problem, seeing as the error code relates to the iommu parameters missing in the boot config.
Is there a way around using the grub.cfg, while getting the passthrough working?

---

