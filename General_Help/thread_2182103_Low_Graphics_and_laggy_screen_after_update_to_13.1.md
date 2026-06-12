---
title: "Low Graphics and laggy screen after update to 13.10 from 13.04"
date: 2013-10-20
forum: General Help
---

### Post by whoru007 on 2013-10-20
Hi Guys,

After updating from 13.04 to 13.10 many of 3D unity stuff has stopped working,

I am suing Samsung Series 3 (NP350V5X) Laptop which has Switchable Intel and AMD Radeon HD 7670M GFX.

**xserver-xorg-video-ati** does works but NO 3D support and graphics are very low. [I am currently using this]
**fglrx & fglrx-updates** shows blank screen after Login.

Intel Graphic Install doesn't work either (dependency error)

Output of $ **sudo lshw -c video**
```
  *-display               
       description: VGA compatible controller
       product: Thames [Radeon HD 7500M/7600M Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:e0000000-efffffff memory:c0120000-c013ffff ioport:3000(size=256) memory:c0100000-c011ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:bfc00000-bfffffff memory:d0000000-dfffffff ioport:4000(size=64)

```

Similarly $ [B]/usr/lib/nux/unity_support_test -p
[/B]```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits)
OpenGL version string:  2.1 Mesa 9.2.1


Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       [B]no
[/B]
```

Shows no 3D support.

Can anyone please guide how to make things working again.

---

### Post by subdir on 2013-10-21
I have exactly the same problem on my Fujitsu LIFEBOOK P771.

$ sudo lshw -c video
```
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:3000(size=64)

```

**/usr/lib/nux/unity_support_test -p **output is the same

---

### Post by grahammechanical on 2013-10-21
This is a clue

> OpenGL render string: Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits)

Gallium is a code name for the Nouveau open source video driver and llvmpipe is a subset of Gallium for use on video cards that cannot render 3D graphics. It is the replacement for Ubuntu 2D. Think of it as a fallback video mode. I suggest that you try to install a proprietary video driver through Additional Drivers. You may need to experiment.

Regards.

---

### Post by subdir on 2013-10-21
This is how I solved my problem

[https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336/comments/19](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336/comments/19)
> [COLOR=#333333][FONT=Ubuntu Mono]I think this command helped me:
sudo pam-auth-update --force
I didn't change anything in dialog that appeared.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Best regards,
Eduard[/FONT][/COLOR]


After I ran ```
[COLOR=#333333][FONT=Ubuntu Mono]sudo pam-auth-update --force[/FONT][/COLOR]
``` and rebooted, Xserver started to use intel video driver.[COLOR=#333333][FONT=Ubuntu Mono]

[/FONT][/COLOR]

---

### Post by whoru007 on 2013-10-23
Well I have to re-install whole OS, things works fine now.

Now output of **/usr/lib/nux/unity_support_test -p** is,

```

OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile x86/MMX/SSE2
OpenGL version string:  3.0 Mesa 9.2.1


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes

```

[s]But I still can't use ATI GFX Card.[/s]

Update: [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics) now allows to use my GFX Card as well.
Simply do,
```
sudo apt-get install fglrx fglrx-pxpress
```

Output of $ **/usr/lib/nux/unity_support_test -p** is,
```
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 7600M Series
OpenGL version string:  4.2.12337 Compatibility Profile Context 13.101


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes

```

---

