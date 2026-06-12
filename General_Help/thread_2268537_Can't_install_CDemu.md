---
title: "Can't install CDemu"
date: 2015-03-09
forum: General Help
---

### Post by ramicio on 2015-03-09
I'm getting the same nonsense as in this thread: [http://ubuntuforums.org/showthread.php?t=2074430](http://ubuntuforums.org/showthread.php?t=2074430)

I follow the steps...nothing.

```
Setting up vhba-dkms (20140629-1ubuntu1~trusty1~ppa1) ...
Removing old vhba-20140629 DKMS files...


------------------------------
Deleting module version: 20140629
completely from the DKMS tree.
------------------------------
Done.
Loading new vhba-20140629 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-50-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
WARNING: Group 'cdrom' already exists.
modprobe: FATAL: Module vhba not found.
ERROR: Unable to load module.
dpkg: error processing package vhba-dkms (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 vhba-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help!

Any why close a thread like that? I could have replied in there, instead of making a new one...

---

### Post by mc4man on 2015-03-09
So you're on 14.04 (trusty) but using the 3.2.0 kernel?? (- which is from 12.04 (precise)

In 14.04 here it builds the module(s) just fine with trusty kernels  - 
> 
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04) ...
Setting up vhba-dkms (20140629-1ubuntu1~trusty1~ppa1) ...
Loading new vhba-20140629 DKMS files...
First Installation: checking all kernels...
Building for 3.13.0-46-generic and 3.16.0-31-generic
Building initial module for 3.13.0-46-generic
Done.

vhba:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-46-generic/updates/dkms/

depmod....

DKMS: install completed.
Building initial module for 3.16.0-31-generic
Done.

vhba:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-31-generic/updates/dkms/

depmod....

DKMS: install completed.

---

### Post by mörgæs on 2015-03-09
> **ramicio said:**
> I'm getting the same nonsense as in this thread: [http://ubuntuforums.org/showthread.php?t=2074430](http://ubuntuforums.org/showthread.php?t=2074430)

...

Any why close a thread like that? I could have replied in there, instead of making a new one...

A lot can happen in the software world in a year so we close threads automatically after that period of time. We don't want to distribute obsolete knowledge.

From the post above it seems that your problem is fixed by now. A fresh install of 14.04.2 would have done the trick.

If a thread has long-time value we sometimes reopen it but not this one.

---

### Post by ramicio on 2015-03-10
I don't know why I'm on that older kernel. I've updated it many times since then. No idea why it's still using such an old one...help?

---

### Post by ramicio on 2015-03-10
Solved. Downloaded .debs of the current kernel and all is fine now. Thanks for your time, everyone!

---

