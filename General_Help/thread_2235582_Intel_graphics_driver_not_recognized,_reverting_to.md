---
title: "Intel graphics driver not recognized, reverting to software rendering"
date: 2014-07-21
forum: General Help
---

### Post by ryanlikesfish on 2014-07-21
Hi folks.  I'm completely new to this.  I am running Ubuntu 14.04 on a new Dell desktop.
I am having a problem with Xorg and compiz using >60% of a CPU.  I think this is because my graphics driver is not being recognized, and so software is being used as the accelerator as opposed to the card.

My card is Intel Xeon E3-1200 v3/4th Gen Core.  Please take a look at the output below and ask me if I am leaving out important information.  I'd be grateful for any advice.  I think the telling lines are the "Not software rendered:    no" and the "(EE) Failed to load module "modesetting" (module does not exist, 0)."

I have updated the Intel driver.

uname -a
```
Linux xxx 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

lshw -c video
```
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

Output of: /usr/lib/nux/unity_support_test -p
```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OpenGL version string:  2.1 Mesa 10.1.3


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


Unity 3D supported:       no

```

Relevant portions of my Xorg.0.log:
```
[    10.871] Loading extension GLX
[    10.871] (==) Matched intel as autoconfigured driver 0
[    10.871] (==) Matched modesetting as autoconfigured driver 1
[    10.871] (==) Matched fbdev as autoconfigured driver 2
[    10.871] (==) Matched vesa as autoconfigured driver 3
[    10.871] (==) Assigned the driver to the xf86ConfigLayout
[    10.871] (II) LoadModule: "intel"
[    10.871] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    10.873] (II) Module intel: vendor="X.Org Foundation"
[    10.873]     compiled for 1.15.0, module version = 2.99.910
[    10.873]     Module class: X.Org Video Driver
[    10.873]     ABI class: X.Org Video Driver, version 15.0
[    10.873] (II) LoadModule: "modesetting"
[    10.873] (WW) Warning, couldn't open module modesetting
[    10.873] (II) UnloadModule: "modesetting"
[    10.873] (II) Unloading modesetting
[    10.873] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    10.873] (II) LoadModule: "fbdev"
[    10.873] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    10.873] (II) Module fbdev: vendor="X.Org Foundation"
[    10.873]     compiled for 1.15.0, module version = 0.4.4
[    10.873]     Module class: X.Org Video Driver
[    10.873]     ABI class: X.Org Video Driver, version 15.0
[    10.873] (II) LoadModule: "vesa"
[    10.873] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    10.873] (II) Module vesa: vendor="X.Org Foundation"
[    10.873]     compiled for 1.15.0, module version = 2.3.3
[    10.873]     Module class: X.Org Video Driver
[    10.873]     ABI class: X.Org Video Driver, version 15.0
[    10.873] (==) Matched intel as autoconfigured driver 0
[    10.873] (==) Matched modesetting as autoconfigured driver 1
[    10.873] (==) Matched fbdev as autoconfigured driver 2
[    10.873] (==) Matched vesa as autoconfigured driver 3
[    10.873] (==) Assigned the driver to the xf86ConfigLayout
[    10.873] (II) LoadModule: "intel"
[    10.874] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    10.874] (II) Module intel: vendor="X.Org Foundation"
[    10.874]     compiled for 1.15.0, module version = 2.99.910
[    10.874]     Module class: X.Org Video Driver
[    10.874]     ABI class: X.Org Video Driver, version 15.0
[    10.874] (II) UnloadModule: "intel"
[    10.874] (II) Unloading intel
[    10.874] (II) Failed to load module "intel" (already loaded, 32548)
[    10.874] (II) LoadModule: "modesetting"
[    10.874] (WW) Warning, couldn't open module modesetting
[    10.874] (II) UnloadModule: "modesetting"
[    10.874] (II) Unloading modesetting
[    10.874] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    10.874] (II) LoadModule: "fbdev"
[    10.874] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    10.874] (II) Module fbdev: vendor="X.Org Foundation"
[    10.874]     compiled for 1.15.0, module version = 0.4.4
[    10.874]     Module class: X.Org Video Driver
[    10.874]     ABI class: X.Org Video Driver, version 15.0
[    10.874] (II) UnloadModule: "fbdev"
[    10.874] (II) Unloading fbdev
[    10.874] (II) Failed to load module "fbdev" (already loaded, 0)
[    10.874] (II) LoadModule: "vesa"
[    10.874] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    10.874] (II) Module vesa: vendor="X.Org Foundation"
[    10.874]     compiled for 1.15.0, module version = 2.3.3
[    10.874]     Module class: X.Org Video Driver
[    10.874]     ABI class: X.Org Video Driver, version 15.0
[    10.874] (II) UnloadModule: "vesa"
[    10.874] (II) Unloading vesa
[    10.874] (II) Failed to load module "vesa" (already loaded, 0)
[    10.874] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    10.875] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    10.875] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    10.875] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    10.875] (II) FBDEV: driver for framebuffer: fbdev
[    10.875] (II) VESA: driver for VESA chipsets: vesa
[    10.875] (++) using VT number 7


[    10.881] (II) Loading sub module "fbdevhw"
[    10.881] (II) LoadModule: "fbdevhw"
[    10.881] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    10.881] (II) Module fbdevhw: vendor="X.Org Foundation"
[    10.881]     compiled for 1.15.1, module version = 0.0.2
[    10.881]     ABI class: X.Org Video Driver, version 15.0
[    10.881] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    10.881] (II) FBDEV(0): using default device
[    10.881] (WW) Falling back to old probe method for vesa
[    10.881] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    10.881] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    10.881] (==) FBDEV(0): RGB weight 888
[    10.881] (==) FBDEV(0): Default visual is TrueColor
[    10.881] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    10.881] (II) FBDEV(0): hardware: VESA VGA (video memory: 9024kB)
[    10.881] (II) FBDEV(0): checking modes against framebuffer device...
[    10.881] (II) FBDEV(0): checking modes against monitor...
[    10.881] (--) FBDEV(0): Virtual size is 1920x1200 (pitch 1920)
[    10.881] (**) FBDEV(0):  Built-in mode "current": 230.4 MHz, 94.7 kHz, 77.4 Hz
[    10.881] (II) FBDEV(0): Modeline "current"x0.0  230.41  1920 1952 2192 2432  1200 1204 1208 1224 -hsync -vsync -csync (94.7 kHz b)
[    10.881] (==) FBDEV(0): DPI set to (96, 96)
[    10.881] (II) Loading sub module "fb"
[    10.881] (II) LoadModule: "fb"
[    10.881] (II) Loading /usr/lib/xorg/modules/libfb.so
[    10.881] (II) Module fb: vendor="X.Org Foundation"
[    10.881]     compiled for 1.15.1, module version = 1.0.0
[    10.881]     ABI class: X.Org ANSI C Emulation, version 0.4
[    10.881] (**) FBDEV(0): using shadow framebuffer
[    10.881] (II) Loading sub module "shadow"
[    10.881] (II) LoadModule: "shadow"
[    10.881] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    10.881] (II) Module shadow: vendor="X.Org Foundation"
[    10.881]     compiled for 1.15.1, module version = 1.1.0
[    10.881]     ABI class: X.Org ANSI C Emulation, version 0.4
[    10.881] (II) UnloadModule: "vesa"
[    10.881] (II) Unloading vesa
[    10.881] (==) Depth 24 pixmap format is 32 bpp
[    10.881] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    10.881] (==) FBDEV(0): Backing store enabled
[    10.882] (==) FBDEV(0): DPMS enabled
[    10.882] (==) RandR enabled
[    10.884] (II) SELinux: Disabled on system
[    10.885] (II) AIGLX: Screen 0 is not DRI2 capable
[    10.885] (EE) AIGLX: reverting to software rendering
[    10.903] (II) AIGLX: Loaded and initialized swrast
[    10.903] (II) GLX: Initialized DRISWRAST GL provider for screen 0

```

---

### Post by grahammechanical on 2014-07-21
This is what I see when I run that unity support test. Can you see the differences?

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.2.3


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

NVA5 = Nvidia code for my Nvidia GT220. Gallium 0.4 = Nouveau, the open source video driver for Nvidia. But you have have llvmpipe (LLVM 3.4, 256 bits). Ubuntu uses llvmpipe as a fall back open source video driver for when a graphic adapter  does not have the capabilities to do 3D rendering in hardware. We also get llvmpipe if you use recovery mode and select the Resume option.

It does not matter if the graphic adapter can do 3D hardware rendering. Once the system is running on llvmpipe that unity support test will say that Unity 3D is not supported. Have you tried going to System Settings>Software and Updates>Additional Drivers tab and changing video drivers?

Line 10.885 (EE) of Xorg.0.log says "reverting to software rendering." I am not an expert in this but my guess would be that X server has failed to detect the optimum video mode for the monitor. Sometimes the only way we can get a Ubuntu live session running and an install boot is to put "nomodeset" as a boot option. Setting a video driver may solve this problem. Fingers crossed!

Line 10.885 (II) says "AIGLX: Screen 0 is not DRI2 capable."  Now, what does that mean?

Edit: Direct Render Infrastructure (DRI)

[http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure](http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure)

[http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/)

[http://www.x.org/wiki/IntelGraphicsDriver/](http://www.x.org/wiki/IntelGraphicsDriver/)

Question: What is the graphic adapter?

Regards.

---

### Post by ryanlikesfish on 2014-07-21
Thanks for the input.

Changing the grub line to "nomodeset" still produced the same result in the Xorg.0.log file: (EE) Failed to load module "modesetting" (module does not exist, 0).
Yes, the key differences in our test results are the first and last lines.  I need to change something so that my "Not software rendered: " answers "yes" and my "Unity 3D supported: " answers "yes."  I am hoping once I fix the issue that leads to failure of the hardware rendering, I will solve the problem with Compiz memory.

You I think you are right, the "Failed to load module "modesetting" (module does not exist, 0)" and the "AIGLX: Screen 0 is not DRI2 capable; AIGLX: reverting to software rendering" are the informative lines.

Can you tell me how to check the "graphic adapter" if that would help?  The driver I have is the i965-va-driver from Intel.  The card is Intel Xeon E3-1200 v3/4th Gen Core.  Yes, all the software updates for "additional drivers" were examined.  None exist.  I updated the intel driver previously using the "intel graphics installer for linux."

---

### Post by ryanlikesfish on 2014-07-22
An update:
[COLOR=#333333][FONT=ClearSans-Light]This issue continues.  Other anomalies I've noted that might be related:[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]My monitor is detected as a "built in display" and the resolution cannot be changed.  I figure this must be related.  (I have an external monitor.)[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Output of  xrandr --verbose:[/FONT][/COLOR]
```
[COLOR=#333333][FONT=ClearSans-Light]xrandr: Failed to get size of gamma for output default[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Screen 0: minimum 1920 x 1200, current 1920 x 1200, maximum 1920 x 1200[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]default connected primary 1920x1200+0+0 (0x17f) normal (normal) 0mm x 0mm[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Identifier: 0x17e[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Timestamp:  173701[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Subpixel:   unknown[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Clones:    [/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]CRTC:       0[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]CRTCs:      0[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Transform:  1.000000 0.000000 0.000000[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]           0.000000 1.000000 0.000000[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]           0.000000 0.000000 1.000000[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]          filter: [/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]  1920x1200 (0x17f)  177.4MHz *current[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]        h: width  1920 start    0 end    0 total 1920 skew    0 clock   92.4KHz[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]        v: height 1200 start    0 end    0 total 1200           clock   77.0Hz[/FONT][/COLOR]

```

---

