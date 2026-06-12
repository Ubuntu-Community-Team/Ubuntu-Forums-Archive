---
title: "Problem with nvidia 1060 driver running laptop display before login (Razer Blade)"
date: 2018-02-01
forum: General Help
---

### Post by sicklybeans on 2018-02-01
I have a 2016 Razer Blade 14" running Ubuntu 17.10 Budgie Remix with nvidia drivers version 384. I had a similar problem on vanilla Ubuntu 16.04 as well.


As is outlined here: [https://help.ubuntu.com/community/RazerBlade](https://help.ubuntu.com/community/RazerBlade), there are known problems switching between the Nvidia 1060 graphics card and the on board intel one.


I wanted to use my laptop with an external monitor, which for the Razer Blade, only works with the nvidia graphics card (see above link). I installed the proprietary nvidia drivers and now my external monitor runs fine. 


However, there is a new problem. Whenever I start up my computer before I log in, the laptop screen is completely blank. The normal Budgie logo appears during boot, but instead of the log in screen, the screen goes dark. If I type in my password and hit enter, then the desktop loads normally.


I then get a "Ubuntu has encountered a problem message" which indicates that something has gone wrong with Xorg. I checked the Xorg output log (/var/log/Xorg.0.log):
```

[    12.755] (II) Module fbdev: vendor="X.Org Foundation"
[    12.755]     compiled for 1.19.3, module version = 0.4.4
[    12.755]     Module class: X.Org Video Driver
[    12.755]     ABI class: X.Org Video Driver, version 23.0
[    12.755] (II) LoadModule: "vesa"
[    12.755] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.756] (II) Module vesa: vendor="X.Org Foundation"
[    12.756]     compiled for 1.19.3, module version = 2.3.4
[    12.756]     Module class: X.Org Video Driver
[    12.756]     ABI class: X.Org Video Driver, version 23.0
[    12.756] (II) NVIDIA dlloader X Driver  384.111  Tue Dec 19 22:25:34 PST 2017
[    12.756] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    12.756] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    12.756] (II) FBDEV: driver for framebuffer: fbdev
[    12.756] (II) VESA: driver for VESA chipsets: vesa
[    12.756] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    12.756] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    12.756] (WW) Falling back to old probe method for modesetting
[    12.756] (EE) open /dev/dri/card0: No such file or directory
[    12.756] (WW) Falling back to old probe method for fbdev
[    12.756] (II) Loading sub module "fbdevhw"
[    12.756] (II) LoadModule: "fbdevhw"
[    12.756] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.756] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.756]     compiled for 1.19.5, module version = 0.0.2
[    12.756]     ABI class: X.Org Video Driver, version 23.0
[    12.757] (WW) Falling back to old probe method for vesa
[    12.757] (EE) No devices detected.
[    12.757] (EE) 
Fatal server error:
[    12.757] (EE) no screens found(EE) 
[    12.757] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    12.757] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    12.757] (EE) 
[    12.807] (EE) Server terminated with error (1). Closing log file.

```



The output of lshw -c video is:
```

  *-display                 
       description: VGA compatible controller
       product: GP106M [GeForce GTX 1060 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:327 memory:dc000000-dcffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:e000(size=128) memory:dd000000-dd07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:319 memory:db000000-dbffffff memory:70000000-7fffffff ioport:f000(size=64) memory:c0000-dffff

```

The output of lsmod | grep nvidia is:
```

nvidia_uvm            667648  0
nvidia_drm             45056  2
nvidia_modeset        860160  5 nvidia_drm
nvidia              13139968  400 nvidia_modeset,nvidia_uvm
drm_kms_helper        167936  2 i915,nvidia_drm
drm                   356352  6 i915,nvidia_drm,drm_kms_helper

```




Thanks

---

### Post by sicklybeans on 2018-02-03
Bump

---

