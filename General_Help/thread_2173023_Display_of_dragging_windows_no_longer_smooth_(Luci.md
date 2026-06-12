---
title: "Display of dragging windows no longer smooth (Lucid)"
date: 2013-09-07
forum: General Help
---

### Post by goodstuff9 on 2013-09-07
I don't know why, suddenly without any cause I can think of when I drag an open window across the desktop, instead of it smoothly moving across the desktop, it moves in a series of "repaintings" is the only way I know to describe it.  

Also, I noticed that when scrolling up and down the menu lists from the task bar it is also no longer "smooth".  

And, when I use two monitors for my display, when I try to drag a window from the main monitor to the secondary monitor, it can go only part way into the secondary monitor, and then I can't drag it any further.  Very odd.  

Anyway, I don't know enough about the display settings stuff to know what would have caused this to suddenly happen, nor do I know how to fix this.  Any help will be appreciated.

---

### Post by newb85 on 2013-09-07
Seems like the behavior mentioned here.  [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178)

What kind of graphics card are you using, and what drivers?  (if you don't know, run the following.)
```
sudo lshw -C display
```

Also, are you aware the Lucid hit End-of-Life five months ago?

---

### Post by goodstuff9 on 2013-09-07
Thanks for the reply.  

I don't know if it is the same problem as that described in the Launchpad link you supplied - I'm not expert enough to completely follow the (pieces of) conversation that was in that thread.  

Yes, I know that Lucid is no longer supported, just haven't had time to mess with the upgrade yet.  

Here is the output of sudo lshw -C display:  

*-display UNCLAIMED     
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff(prefetchable) memory:fdcc0000-fdcdffff ioport:dc00(size=256) memory:fdca0000-fdcbffff(prefetchable)

---

### Post by newb85 on 2013-09-07
The behavior is similar, but the bug report was for nVidia GPUs, and yours is ATI.  You're using the generic graphic drivers.  I would suggest that you try installing the proprietary ATI drivers, but I'm not experienced with that, and what's more, lshw didn't return any info on the graphics card beyond the make.  Maybe someone else would have a better idea.

---

