---
title: "Multiple kernels Ubuntu installed Feisty"
date: 2007-05-29
forum: General Help
---

### Post by stchman on 2007-05-29
Hello all, I was playing around in Synaptic and I noticed that there are a lot of different kernels.  Each one takes about 70MB and such.

I am currently using the 2-6-20-16-generic kernel with no difficulties.  Can I uninstall all the other kernels since they are not being used?  It would free up several hundred MB.

Thanks

---

### Post by merlinus on 2007-05-29
Yes, and using synaptic is the safest way.

This might happen automatically, but if not --

remove the kernel entries in /boot/grub/menu.lst

-merlin

---

### Post by stchman on 2007-05-29
> **merlinus said:**
> Yes, and using synaptic is the safest way.

This might happen automatically, but if not --

remove the kernel entries in /boot/grub/menu.lst

-merlin

Cool, I have a PC running Feisty that I rarely use.  I will try removing all the kernel other than the one I am using.  I will report back here what happens.  If I hose that machine then oh well.  It looks like it will free up about 300MB of disc space.

---

### Post by stchman on 2007-05-30
It worked, I freed up over 250MB after I uninstalled all the extra kernels through synaptic.

---

### Post by ronmarley1 on 2007-05-30
For future reference, it may be advantageous to have the current kernel and the one previous.  That way, if the new one gives you issues, you can always boot the previous.  For example, from reading these forums, some folks are having issues with the -16 kernel.

---

