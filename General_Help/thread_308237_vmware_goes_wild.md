---
title: "vmware goes wild"
date: 2006-11-27
forum: General Help
---

### Post by pieroxy on 2006-11-27
I have an ubuntu running at work fine, with an XP virtualized just great. Even thought the upgrade to Edgy was... a bit hectic, I decided to run for it at home. The plan was to have a vmware running WinXP to ease the pain on my other half.

The problem is that I can't seem to get it running. In appearance, everything is fine. I installed Edgy on my machine and all went smoothly, and all still is. I installed vmware server 1.0.1 that gave me the warning:

```
Unable to compile the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed.  Errors encountered during 
compilation and installation of the module can be found here: 
/tmp/vmware-config0

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file: 
'/tmp/vmware-config0/control-only/make.log'
********
```

I still don't think it's that big of an issue. But who knows.

From there, vmware seemed to be working. But I try to install a WinXP (that I've installed several times even in a VM) and it went horribly wrong. Everything broke from the installer on... I did it again, and better luck this time. But the SP2 broke it once more. Tried again to have a system that seems to be working. And then my VM closed unexpectedly with a horrible message...

I tried to install an Edgy in a VM too. Everything breaks: Firefox every minute, I downloaded a JDK from sun, and it doesn't even allow me to execute it complaining the dl has been corrupted, even though I've installed the very same file in the host Edgy !!! Synaptic crashed on me both times I've tried it...

Any clues as to why vmware is doing this?
Any help on resolving these issues?

Thanks a bunch

---

### Post by pieroxy on 2007-01-23
Bad memory module. Problem fixed.

---

