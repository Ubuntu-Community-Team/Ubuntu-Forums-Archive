---
title: "Problem with OpenGL Version and Skylake HD Graphics 510"
date: 2016-08-23
forum: General Help
---

### Post by aargonian on 2016-08-23
Hello all, first time posting to the forums despite much time spent lurking.

I am currently running into a rather frustrating issue with my current graphics configuration on Ubuntu. The graphics card in my system is an integrated HD Graphics 510 from Intel, and is supposedly capable of supporting OpenGL 4.4/DirectX 12. I am wanting to learn OpenGL 4.3 development, so that works out just fine for me. Problem is, glxinfo seems to report that I only have an OpenGL 3.3 profile. This doesn't match up with the information I found about the HD Graphics 510 capabilities. All searches regarding upgrading OpenGL version also indicate that Ubuntu should be capable of figuring out what version of OpenGL my driver supports and automatically does the correct configuration and driver installation. 

So basically, I'm asking if I have the information wrong here. Am I misinterpreting the information I found on the HD Graphics 510, or do I truly have a mismatch problem here with my hardware/software? I don't want to go poking at the drivers and swapping them or anything until I get some more advice on this, as I've spent an extensive amount of time setting this machine up the way I like it after a couple of years of playing with various OSes and tools. That said, I do need OpenGL 4.3 or higher to do the development I want, and I am willing to tear the machine apart *if I have to*. All of my data is backed up, and I'm not afraid to risk borking the machine and having to do a complete reinstall if that is what it takes, but I'd rather avoid the pain if I don't have to. If there is some step I can take to upgrade my OpenGL version, I'm willing to give it a try. I've considered upgrading the kernel as well, but I haven't gone that far yet. 

Information about my system is as follows:

Kernel Version: 4.4.0-34-generic
Ubuntu Version: 16.04



The output of "glxinfo | grep OpenGL" is as follows:
```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 510 (Skylake GT1) 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 11.2.0
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 11.2.0
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 11.2.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:
```

Furthermore, the output of "lspci -nnk | grep -i vga -A3" returns the following information about the video card:

```

00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:1902] (rev 06)
    DeviceName:  Onboard IGD
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7998]
    Kernel driver in use: i915_bpo

```

As can be seen, I am using the i915_bpo driver, which if I'm not mistaken means I am using a backported version of the i915 driver that is used for all intel graphics cards. If I am incorrect on that, please let me know. 

Output from "lshw -c video":
```

  *-display               
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:317 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64)

```

If any more information is needed, I can add it here or list it in a comment. Any help is appreciated, and many thanks in advance!

---

### Post by aargonian on 2016-08-23
Problem solved. A little more research has turned up that although the integrated graphics do support OpenGL 4.4, the support has not yet been implemented in Mesa, and is still limited to OpenGL 3.3 for the time being. Guess I'll just have to wait this one out for now.

---

