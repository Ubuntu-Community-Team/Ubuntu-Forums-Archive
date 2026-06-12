---
title: "Linux 3.8.8 Kernel on 12.04LTS"
date: 2013-04-19
forum: General Help
---

### Post by speartip on 2013-04-19
I have just installed the above kernel on my LTS system from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
as it seems to run a lot smoother and faster on my Intel setup. (apparently lots of improvements in the 3.8 kernel)
I also install the linux-firmware, package from here:
[http://packages.ubuntu.com/raring/linux-firmware](http://packages.ubuntu.com/raring/linux-firmware)
as my system squealed about "possible missing firmware"
This seemed to resolve the issue.
My question is, have I now compromised the stabilty of my LTS system by installing 13.04 packages, or should I be ok?

---

### Post by matt_symes on 2013-04-19
Hi

> My question is, have I now compromised the stabilty of my LTS system by installing 13.04 packages, or should I be ok?

That really depends on whether there are any bugs in the packages you install. They should be binary compatible.

I have been using the newest kernel version from mainline in a Quantal for a good while with no obvious problems.

Kind regards

---

### Post by speartip on 2013-04-19
Thanks Matt..
Everything seems ok & as mentioned probably runs even better.
So i'll stick with this setup, unless I notice any regressions.

---

