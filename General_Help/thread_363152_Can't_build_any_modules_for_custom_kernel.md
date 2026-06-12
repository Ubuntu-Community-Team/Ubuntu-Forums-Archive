---
title: "Can't build any modules for custom kernel"
date: 2007-02-16
forum: General Help
---

### Post by cookfromfrozen on 2007-02-16
HI

I downloaded kernel 2.6.19.2, compiled and installed it.

When running the kernel however, I can't seem to be able to compile any modules for the kernel.  The kernel source is still under /usr/src/linux (which is a symlink to /usr/src/linux-2.6.19.2).

I've tried compiling various things:  the latest Madwifi, Truecrypt, the VMware kernel modules.  They all recognise that the source for the current kernel is kept in /usr/src/linux (which it is), but they all fail with nondescript errors (make [Error 2]).

I have run make modules_prepare from inside /usr/src/linux, but to no avail.

What could I be missing?  When I build the kernel, I copied over my current config and didn't change anything, so is there a kernel config option I am missing or something?

Thanks in advance.

---

### Post by orb9220 on 2007-02-19
This is the guide I just used on edgy.

[http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/](http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/)

---

