---
title: "Ubuntu 7.10 and VirtualBox from synaptic start problem."
date: 2007-11-19
forum: General Help
---

### Post by frodemt on 2007-11-19
Hi there.

I have a problem with Virtual Box. When I hit the start-button inside the program I get this message:


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

I have tried to run /etc/init.d/vboxdrv start as root, but that wont work. There is no file names vboxdrv. I installed the program from synaptic.

Does anyone have any suggestions?

---

### Post by LazyTownRocks on 2007-11-24
I had that same thing too, went away after I rebooted then deleted and re-creatd the vitual machines .... only to then be replaced with ...

__________________________________________________________________________________
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
__________________________________________________________________________________

... I've checked the group and the users are in there .... ?????

---

### Post by LazyTownRocks on 2007-11-24
.... now sorted that one, had to select the tick-boxes in the vboxuser group in user admin/groups and then select the 'vboxuser' group to give appropriate permissions for the user and app to access ...

... hopefully the above will help you too.

Laz.

---

### Post by frodemt on 2007-12-02
Thank you. It seems to work now.

But it is three times slower than vmWare is in windows. How come? I allocated same amount of memory.

---

### Post by frodemt on 2007-12-05
bump

---

