---
title: "Flickering Screen. Ubuntu 16.04"
date: 2017-07-05
forum: General Help
---

### Post by ljetibo on 2017-07-05
Can you post a bit more on the exact steps you took? I've tried several suggestions I've found on the net and none of them worked for me at all. Specifically I've tried doing the suggested ppa graphics-drivers installations for 352, 375 and 381 (and probably some others as well but I forgot). I've also tried doing the compiz configure settings workaround. Neither of them helped me. Whenever I'm working, moving my mouse or having any kind of active loading icon running somewhere on the screen (visible) everything is normal. The second the screen doesn't need to "update" the horrendous blinking begins. 

I've tried installing kernel 4.4 by following this tutorial but it hasn't worked for me: [http://linuxdaddy.com/blog/install-kernel-4-4-on-ubuntu/](http://linuxdaddy.com/blog/install-kernel-4-4-on-ubuntu/)

this is my lhsw:

```

  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:f5000000-f5ffffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: GM108M [GeForce 940M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:51 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f7000000-f707ffff

```

any help is appreciated since I need ubuntu for work.

---

### Post by QIII on 2017-07-05
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2356878").

Hello!

Tagging on to a thread marked "Solved" is not likely to draw a lot of help your way.  People usually loot at solved threads for answers, not to lend assistance.  The original poster is certainly not likely to be interested in the thread any longer.

Cheers!

---

### Post by ljetibo on 2017-07-05
Oh, ok, sorry. You're right, I haven't checked his last activity log and didn't notice he's not around anymore.

---

### Post by ljetibo on 2017-07-06
To make a small update. I could not figure out how to deal with the buggy Intel and nVidia drivers in the 16.04LTS and have therefore reverted back to 14.04. 
For an unknown reason the Intel drivers there at least seem to be functioning normally and there is no blinking. 
I have installed the 4.11.9-041109-generic kernel manually to remove various acpi bugs (fn+f5/f6 etc...) and will probably remain here for the foreseeable future. 
Installing the proprietary nVidia drivers makes the whole screen go black at login and they have to be purged in tty so be warned if not in familiar territory. 

Any help or anyone willing to experiment and help me debug the 16.04LTS I'm willing to do yet another OS install (next to Win and the Ubuntu 14.04) to play around. I don't think this is a particularly good solution but it's much better than constantly running a gif in the background to stop the blinking.

---

