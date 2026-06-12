---
title: "Virtualbox error"
date: 2008-04-23
forum: General Help
---

### Post by ikki_72 on 2008-04-23
Tried to run virtualbox and got this error:> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
How do i install the vbox kernel module anyway?

---

### Post by ikki_72 on 2008-04-23
I did
> sudo depmod -a
sudo /etc/init.d/vboxdrv start then it's ok.

---

