---
title: "Problems with Virtualbox OSE"
date: 2008-06-18
forum: General Help
---

### Post by Landscapeman on 2008-06-18
I have downloaded and trying to run windows on my computer. I need it for Quickbooks.

Error Message:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

How do I rectify this problem? Thanks

---

### Post by omegamike3 on 2008-06-18
Go to Synaptic Package Manager, search for "virtualbox" and install the virtualbox-ose-modules package corresponding to your kernel version. You can also install the "generic" one as well. You can find out your kernel version by opening a terminal and typing: ```
uname -r
```

---

### Post by Landscapeman on 2008-06-18
I have 2.6.24-19-generic. I am unable to find the right one. Which generic one?

---

### Post by Landscapeman on 2008-06-18
I found the module and I installed it and it still doesn't work any ideas? Thanks

---

