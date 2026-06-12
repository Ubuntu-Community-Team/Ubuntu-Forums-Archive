---
title: "Clean Install of Kubuntu 16.04 Extremely Slow Graphics - Please help"
date: 2017-02-04
forum: General Help
---

### Post by jabog6 on 2017-02-04
Hi,

My PC is brand new, has an Intel i3-7100 CPU, 16GB RAM, SSD.  No dedicated GPU.

I did a clean install of Kubuntu 16.04, and am struggling with the graphics.  I had the same problem with Ubuntu, Ubuntu Gnome and Ubuntu/Cinnamon.  The windows are very slow to refresh.  If I drag a window across the screen, it gets very choppy.  Videos are also unwatchable... :(

The kicker is that when I first installed Kubuntu on it, 2 weeks ago, I had this issue and installed the "Intel Graphics Update Tool" which (if I remember) did the trick.  I don't remember doing anything other than the Intel tool, and maybe disabling some of the Desktop Effects.  At that time, the graphics were fine, I could watch movies, etc.  Now I re-did a clean install (I wanted to try other flavors of Ubuntu) and I can't get the graphics to work again!  

So, I know it's possible to get to graphics with my hardware, but I don't know how to do it...  I've spent hours looking into it, and can't figure it out.  Please help!

Thank you.

More info:
```
lspci command output includes:
00:02.0 VGA compatible controller: Intel Corporation Device 5912 (rev 04)

Kinfocenter lists "Gallium on llvmpipe (LLVM 3.8, 256 bits)" under "Renderer", and "unknown" under "3D Accelerator".
```

What other info can I provide?

Thanks in advance!

Even more info:
```
lshw command out put includes:*-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64)
```

I don't know if any of the above can help explain the problem.  I'm getting desperate. :)  Please help if you can.

---

### Post by Autodave on 2017-02-04
Have you tired going onto the update area and seeing if the OS can find a better driver than the default one?

Let it search and try the one that's recommended: if it finds any.

---

