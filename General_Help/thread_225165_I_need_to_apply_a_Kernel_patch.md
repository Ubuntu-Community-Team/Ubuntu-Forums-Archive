---
title: "I need to apply a Kernel patch"
date: 2006-07-29
forum: General Help
---

### Post by Face1 on 2006-07-29
I want to use a program that needs me to path my kernel, suspend2.  However, I do not know where to get the kernel source.  I know I can get the newest kernel version source from kernel.org, and then follow [these instructions]("http://ubuntuforums.org/showthread.php?t=217657"), but that does not take into account the ubuntu kernel patches (which I believe exist).  For example, I know that the recent(-ish) kernel update available through the repositories fixed my problem with my sky2 NIC card, and I'm under the impression that this is not due to a change in the actual kernel, but it is due to a change in the ubuntu kernel patching.  

So is it possible to get the patched kernel source instead of just the image?  Or even better, is there a way apply the ubuntu patch(es) to the newest kernel on kernel.org to take advantage of new features, but also have the ubuntu fixes?

---

### Post by Face1 on 2006-07-30
Can someone help me here please?

---

### Post by o_fortuna on 2006-07-30
To get the kernel sources (with ubuntu patches applied), install the package "linux-source"

From the terminal, that's:
```
sudo aptitude install linux-source
```

Or, look for it in System--Administration--Synaptic Package Manager.

Once installed, you'll find the source in usr/src/linux-source-2.6.15.tar.bz2

---

### Post by Face1 on 2006-07-30
Thank you, that was very helpful.  Any word from anyone on applying patches on newer kernels?

---

### Post by Face1 on 2006-07-30
Well, I did that and got the patched source, but then ran into a problem.  Appearently (I think), the ubuntu patches conflict with the suspend2 patch that I am attempting to apply:```
jacob@lappy:/usr/src/linux-source-2.6.15$ sudo ../suspend2-2.2-rc16-for-2.6.15/apply
Applying 100-suspend2-2.2-rc16-for-2.6.15.patch ...
100-suspend2-2.2-rc16-for-2.6.15.patch will not apply cleanly. Reverse applied patches [Yn]?

```

So now it appears I ought to just get the newest kernel source and then apply the newest suspend2 patch, and not use the ubuntu patches.  What are the disadvantages to doing this?  I'm pretty sure that I might lose sky2 support, which is not really acceptable to me.  Any other way of doing this maybe?

---

### Post by Face1 on 2006-07-30
Well I just found [this thread]("http://ubuntuforums.org/showthread.php?t=221088"), which looks like it has exctly what I need...I should have mentioned that I was trying to use suspend2 earlier..oh well.

---

