---
title: "[USB] VMWare Windows grabs USB all the time!! Ubuntu priority?"
date: 2008-05-29
forum: General Help
---

### Post by kakyoism on 2008-05-29
My Windows on VMWare always grabs the USB devices so that Ubuntu
can't use it anymore. Is there a way to let Ubuntu have higher priority
in detecting and owning USB devices?

thx!

---

### Post by CameO73 on 2008-05-29
Not a real solution, but you could use [VirtualBox](http://www.virtualbox.org/wiki/VirtualBox) (another virtual machine manager). In VirtualBox you have to manually select which USB devices you want to use in the VM (or want to release).

---

### Post by Vadi on 2008-05-29
Don't think so, or you'd have trouble getting a USB device in VMware then. The 'proper' way would be to close the vmware machine, plugin, and start it.

---

