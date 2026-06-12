---
title: "VMware Still Require Re-do after kernel update?"
date: 2006-11-05
forum: General Help
---

### Post by mark2741 on 2006-11-05
I used VMWare Server 1.0 Beta for a while when it first came out to host a Windows XP image on my Ubuntu machine. It worked great but eventually I got tired of having to re-run the vmware configuration (I think that was what it was called) every time a kernel update occurred (which is fairly frequent as you know). 

I know that VMWare Server is now out of beta and was wondering if this issue of having to go through that config process is still required for the latest version, whenever a kernel update is run?

---

### Post by David Corrales on 2006-11-06
You'll need to do if the kernel number changes. Else, the headers will stay the same and there's no problem.

---

### Post by mark2741 on 2006-11-06
Is that the same as it was with the Beta version too? Or was the Beta requiring for both headers and version numbers and the full release is not requiring both?

> **David Corrales said:**
> You'll need to do if the kernel number changes. Else, the headers will stay the same and there's no problem.

---

### Post by maslian on 2006-11-06
It has nothing to do with the vmware release, it's related to the new kernel, because when you update your kernel it doesn't create the modules needed by the vmware-server. Either Beta or Final it's the same and i guess you will have to do this "RE-DO" always because VMware is commercial and probably doesn't want an automatic  creation of the kernel-modules.

---

### Post by AndyCooll on 2006-11-06
Unfortunately you will need to re-run the VMware install script each time the kernel is updated. The reasons for which have been explained above.

:cool:

---

### Post by David Corrales on 2006-11-07
Again, you'll need to rebuild -only- if the version changes. That's because a version change, implies a header and version change so the modules are not properly "synced".
On the other side, if you upgrade the kernel, but it's version remains the same (i.e. a security patch) then you'll have no problems since the headers stay the same, only the method implementation changes.

---

### Post by anaconda on 2006-11-07
You dont have to get every kernel upgrade! I wont. it is too much hassle to reconfigure VMWare and Nvidia drivers each time..

---

### Post by David Corrales on 2006-11-07
> **anaconda said:**
> You dont have to get every kernel upgrade! I wont. it is too much hassle to reconfigure VMWare and Nvidia drivers each time..

Another valid option as long as the fix doesn't concern you directly. Just lock the package in synaptic.

---

