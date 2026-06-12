---
title: "Super slow reboot after adding key using mokutil"
date: 2021-08-10
forum: General Help
---

### Post by csete on 2021-08-10
I wanted to use VMWare Player on my Ubuntu 21.04 laptop, so today, I followed steps (eg. [https://kb.vmware.com/s/article/2146460](https://kb.vmware.com/s/article/2146460)) to add a new signing key to the secure boot shim using mokutil as described here:  [https://kb.vmware.com/s/article/2146460](https://kb.vmware.com/s/article/2146460).   I was successful in getting VMWare player to function properly, however since then my shutdown, restart or boot sequences have slowed to a crawl showing a scrolling screen where all (or most) of the lines start with mok.c.  It looks like this is related to the custom signing key and the secure boot shim.  My question is whether there is any way to fix the slow boot sequence while maintaining the custom signing keys?  If so, can someone point me in the right direction?

Thanks,
Craig

---

### Post by csete on 2021-08-11
Turns out this was my fault.  I had turned on verbosity of the shim based on some steps I followed and that was the cause of the output.  Setting verbosity false again cleared things up.

---

