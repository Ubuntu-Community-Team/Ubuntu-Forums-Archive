---
title: "Obtaining kernel linux-source-2.6.15-26.46"
date: 2006-11-13
forum: General Help
---

### Post by kweiner on 2006-11-13
My newly installed Ubuntu 6.06 is not able to detect its network.  To resolve this, I'm trying to install a new network driver, e100, which requires kernel source to be available in order for me to compile it.  My kernel is version 2.6.15-26.46.  Since I have no network, I can't use synaptic, but I can transfer files via a USB stick.  Can anyone tell me if there is a way for me to download the sources from a Windows machine and then move it to my Ubuntu machine for installation?  Are the sources available as a .deb file somewhere?  If not, how do you install them?

---

### Post by bhirning on 2006-11-13
[http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

this may help

---

### Post by Ramses de Norre on 2006-11-13
That's a ubuntu kernel, no?
If so these will do I think:```
sudo aptitude install linux-headers-`uname -r` kernel-headers-`uname -r`
```

---

### Post by kweiner on 2006-11-13
Yes, it is an Ubuntu kernel, so I can't get it directly from [www.kernel.org](www.kernel.org).  Also I can't get it via aptitude because my NIC isn't detected (the whole reason I am trying to get a hold of the kernel sources).  That's why I was hoping I could find something like a linux-source-2.6.15-26.46.deb file which I could transfer to my Ubuntu installation with a USB drive.  linux-source-2.6.15-26.46 shows up in the list of packages in Synaptic, but I don't know how to figure out where it would get downloaded from if my internet connection was actually working.  Thanks for the help so far.  Any other ideas?

---

### Post by Ramses de Norre on 2006-11-14
You can browse through the packages [here](packages.ubuntu.com), download the packages I mentioned there and use ```
sudo dpkg -i package_name.deb
``` to install them.

---

### Post by kweiner on 2006-11-15
Thanks for your help.  With the link you provided, I was able to find the right .deb packages, transfer them to Ubuntu, and install them.  I was even able to compile the e100 network driver, but it turned out that it didn't help.  I think I am suffering from limitations with an older kernel that doesn't support my hardware. Sigh...

---

