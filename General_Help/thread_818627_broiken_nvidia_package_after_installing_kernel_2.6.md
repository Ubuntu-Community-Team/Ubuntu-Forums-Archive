---
title: "broiken nvidia package after installing kernel 2.6.24-18"
date: 2008-06-04
forum: General Help
---

### Post by torpidnotion on 2008-06-04
Hello all, I just recently updated to 2.6.24-18 and upon rebooting, X couldn't find the nvidia driver.

I rebooted with the 2.6.24-17 kernel and everything was peachy.  I read in a forum post about deleting previous kernel versions, which I did to see if that helped, so I purged 2.6.24-17.

I tried to download the linmux-restricted-modules-2.6.24-18 package, and it said:

The following packages have unmet dependencies: 
linux-restricted-modules-2.6.24-18-generic: Depends: nvidia-kernel-common but it is not installable

Now, I'm trying to revert to 2.6.24-17 and get the restricted-modules package but that says its broken also.  As of right now, I have no video except the default X failsafe.

Please help, and thanks in advance.

---

### Post by fragos on 2008-06-04
It appears that you have used alternate methods like compiling to install Nvidia drivers. System-> Administration-> Hardware Drivers allows you to opt for the proprietary Nvidia drivers. If you had done that you would have all the appropriate packages and they all would have been updated to -18. Hopefully you're using the Synaptic package manager. It does a good job dealing with dependancies from the Ubuntu repositories.

---

### Post by ohiomoto on 2008-06-04
There seems to be some sort of conflict with today's kernel-18.  Here is the post that put up earlier:

[http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

It seems to have helped a few others.

---

### Post by Robocoastie on 2008-06-04
> **fragos said:**
> It appears that you have used alternate methods like compiling to install Nvidia drivers. System-> Administration-> Hardware Drivers allows you to opt for the proprietary Nvidia drivers. If you had done that you would have all the appropriate packages and they all would have been updated to -18. Hopefully you're using the Synaptic package manager. It does a good job dealing with dependancies from the Ubuntu repositories.

that is so not true. That works fine with 7.10 but I (and many many others here) have not been able to get that to work with 8.04.

---

### Post by oldos2er on 2008-06-04
Open System, Administration, Software Sources, and make sure 'Proprietary drivers for devices' is checked under 'Downloadable from the Internet.'

---

