---
title: "Need flash/java etc in ies4linux install"
date: 2008-05-09
forum: General Help
---

### Post by metalguy639 on 2008-05-09
I need flash, java and other stuff with this ies4linux install I have on this machine. I'm running Ubuntu 7.10 on the PC in 32 bit and I need to be able to not have ies4linux stall when loading a page with flash, java or the like. The pages are never loading at all. I'm a web designer so its crucial to have this installed somehow. For the record IE Tab only works in windows, I already tried to install vmware to no avail - (This is also useless since I cannot get a registration code for it do you have to pay for this program it seems so) & The User Switch Agent does absolutely nothing at all - its useless. So please do not suggest these. I need a fully functioning IE install of some kind on the machine without doing a dual boot I would prefer NOT to have virus crap and windows on the PC.

---

### Post by mardawi on 2008-05-09
I don't know about ies4linux, but if i were you i would install windows xp on virtual-box or vmware server. To install virtual box write in terminal:
```

sudo apt-get install virtualbox

```

And then install windows XP on a virtual machine.

---

### Post by metalguy639 on 2008-05-09
> **mardawi said:**
> I don't know about ies4linux, but if i were you i would install windows xp on virtual-box or vmware server. To install virtual box write in terminal:
```

sudo apt-get install virtualbox

```

And then install windows XP on a virtual machine.

Sorry but as I said above I tried the vmware and it did not work. I also tried installing the virtual box and it also does not work on the machine. I get the following message when I try to start everything up and try to install stuff. 

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

So that is most likely not gonna work either as I've tried installing drivers and get nothing.

---

### Post by metalguy639 on 2008-05-24
Is there a fix for the virtualbox install with the error notice I put above? Does anyone know what drivers it is referring to and where I'm supposed to get them. I installed this via the synaptic package manager.

---

