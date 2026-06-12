---
title: "Display resolution"
date: 2024-08-24
forum: General Help
---

### Post by mksundaram2 on 2024-08-24
Hi everyone,
I'm running a dual-boot setup with Windows and Ubuntu 20.04 on my PC. My graphics card supports a 1600x900 (16:9) resolution, which works perfectly on Windows. However, on Ubuntu, I only have three resolution options: 800x600 (4:3), 848x480 (16:9), and 1024x768 (4:3). Unfortunately, none of these options match my monitor's native resolution.
Is there a way to enable 1600x900 (16:9) resolution in Ubuntu 20.04? Any help or guidance would be greatly appreciated!


**P.S.** I’m also using a dual-monitor setup. The integrated graphics card is connected to one monitor, while the installed dedicated graphics card is connected to the other.


Do I need to provide any additional information to help resolve this issue? If so, please let me know, and kindly provide me with step-by-step instructions on how to gather that data using terminal commands.
Thanks in advance!

Here is the output of sudo lshw -C display
 *-display                 <----------------------------------------------------------------------- this is having problem with resolution in Ubuntu.
       description: VGA compatible controller
       product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=radeon latency=0 resolution=1024,768
       resources: irq:34 memory:e0000000-efffffff memory:f7d20000-f7d3ffff ioport:e000(size=256) memory:c0000-dffff
  *-display
       description: VGA compatible controller
       product: 4th Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb1
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: irq:33 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff

---

