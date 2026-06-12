---
title: "computer freezes on update"
date: 2013-01-29
forum: General Help
---

### Post by max littlemore on 2013-01-29
Hi all

I'm using Xubuntu 12.04

I tried to do an update yesterday using the update manager and it got most of the way through applying the changes before the entire machine froze. The only way to get it working was to hard reset.

Today I tried to run synaptic to install a few things and I was reminded that the last update failed. When I ran dpkg --configure -a, the machine froze again. After turning it off an on again, the /var/log/dpkg.log didn't look very useful so I captured the output of the above command to a file. (dpkg --configure -a > ~/dpkg.log)

Here is the result:

```
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.2.0-36-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-36-generic
Building for architecture x86_64
Building initial module for 3.2.0-36-generic
```


So it looks like a problem with the wireless driver and for some reason building an update is freezing the machine. According to the jockey, the broadcom proprietary driver is not enabled.

Any help with this would be fantastic, even if it's just a way to cleanly be able to install packages again...

---

