---
title: "restricted mogules"
date: 2007-01-28
forum: General Help
---

### Post by Doug11 on 2007-01-28
How do I make sure the restricted modules is enabled in /etc/apt/sources.list...I can bring it up with the gedit command, but how can I tell if they are enabled. If they aren't, what do I have to do to enable them. 

I keep getting this error when I do this

doug@home:~$ sudo apt-get install linux-restricted-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.19.1


Any deas? Thx

---

### Post by andreas64 on 2007-01-28
Hi,

please add the universe and multiverse repositories to your /etc/apt/sources.list and do a 'sudo apt-get update'

Andreas

---

### Post by Delkster on 2007-01-28
Hi,

> **Doug11 said:**
> E: Couldn't find package linux-restricted-modules-2.6.19.1
Where did you install your kernel from? Your user information says "Ubuntu 6.10 Edgy User", but Edgy only offers version 2.6.17 of the kernel. Likewise, the Ubuntu repositories only have the restricted modules packages that correspond to the available kernels. For Edgy the latest one would be linux-restricted-modules-2.6.17-10-generic (for the generic kernel). If you've installed a newer kernel separately from somewhere else, you'll need to get the restricted drivers separately as well.

Furthermore, there isn't a package that would be called exactly "linux-restricted-modules-<kernel-version>" -- the package names also have the processor architecture for which the kernel and the modules have been compiled. For the generic kernel that would be linux-restricted-modules-<kernel-version>-generic (e.g. linux-restricted-modules-2.6.17-10-generic, if you have a generic 2.6.17-10 kernel). For the 386 kernel the restricted modules package would be linux-restricted-modules-<kernel-version>-386.

Hope that helps a little.

---

