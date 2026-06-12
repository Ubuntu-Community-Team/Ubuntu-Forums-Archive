---
title: "Kernels, Chromebooks, and Touchpads (oh my!)"
date: 2016-04-03
forum: General Help
---

### Post by xmbwd on 2016-04-03
I have a perfectly functioning [Toshiba Chromebook 2]("https://en.wikipedia.org/wiki/Chromebook#Toshiba_CB35-B3340") running Ubuntu 15.10 under the 4.1.2-040102-generic kernel.  Everything that often does not work on a Chromebook works: sound; keyboard; screen; networking; and touchpad. * But* to use the (*truly awesome*) [Systemback]("https://answers.launchpad.net/systemback") app, I need AUFS support.  The mainline kernel I'm using doesn't have it.  And the "stable" kernels, which do have AUFS support, somehow kill my touchpad when I boot into them.  

It seems to be the case that the kernel forces the synaptics driver to not load.  When I type ```
synclient
``` into terminal, I get this:

```
Couldn't find synaptics properties. No synaptics driver loaded.
```

Can anyone can help me figure out why kernels like 4.2.0-34-generic, running on the same exact computer with the same exact files, somehow stops synaptics from loading --- and how to fix it?

I tried the suggestion [here]("http://ubuntuforums.org/showthread.php?t=2217553"), to add this line to grub:

```
GRUB_CMDLINE_LINUX="i8042.nomux=1 locale=fr_FR i8042.reset"
```

but it had no effect.

Optimally, I could fix the touchpad issue so that it works with different kernels.  The alternative, which I am exploring now, is adding AUFS support to a kernel.  We'll see which one gets fixed first....

---

### Post by xmbwd on 2016-04-07
Awww, come on.  Someone must have an idea?

---

### Post by xmbwd on 2016-04-12
I would really like to know how to get the touchpad fixed, but AUFS came first.  

[Here is a great guide]("http://zackreed.me/articles/90-ubuntu-14-04-with-4-0-4-kernel-and-latest-aufs-from-source") to compiling a kernel with AUFS support.  After trying a few other guides, this one was by far the best.  It just worked.  

So, 1/2 the question is resolved.  I'm leaving this open in the hopes that someone knows the answer to the touchpad/kernel issue.

---

