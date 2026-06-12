---
title: "screen is half black in all screen recording apps"
date: 2023-08-23
forum: General Help
---

### Post by rubinglen-b on 2023-08-23
Crazy problem here when I try to use any screen recording software, half the screen is diagonally bisected and showing up black.  I am trying to record in an x login session since the screen was totally black when i tried to record while in wayland.   Any idea what's going on here?  thanks!

pic [https://drive.google.com/file/d/1838vjWULkgBXrWpyna1vs4RlzmOrT0ac/view?usp=sharing](https://drive.google.com/file/d/1838vjWULkgBXrWpyna1vs4RlzmOrT0ac/view?usp=sharing)
[IMG]https://drive.google.com/file/d/1838vjWULkgBXrWpyna1vs4RlzmOrT0ac/view?usp=drive_link[/IMG]
[IMG]https://drive.google.com/file/d/1838vjWULkgBXrWpyna1vs4RlzmOrT0ac/view?usp=drive_link[/IMG]

---

### Post by TheFu on 2023-08-24
Please be more specific. 
Which apps have you tried?
Which OS are you running?
Which release are you running?
Which GPU/driver is being used?
What content is being recorded? Does it include DRM?

I can't see anything at that screenshot. Sorry.

---

### Post by rubinglen-b on 2023-08-24
I have tried ubuntu stock screen recorder, simple screen recorder, and kooha.  I am running Ubuntu 22.04.3 with kernel 5.19.17 cpu: AMD Ryzen5 and GPU: AMD 6600xt navi23.  I am just trying to record my screen anything i try to record has the same result whether it is my browser or just an empty screen.  

I installed amdgpu driver from here: [COLOR=#E83E8C][FONT=SFMono-Regular]https://repo.radeon.com/amdgpu-install/5.4.2/ubuntu/jammy/amdgpu-install_5.4.50402-1_all.deb
[/FONT][/COLOR]which is not the most current driver, but needed in order to be compatible with PyTorch and rocm. using the 5.19.17 kernel also for compatiblity reasons with pytorch.

output from lshw -c video is as follows:

[FONT=lucida console]
[/FONT][FONT=lucida console]  *-display                 [/FONT]
[FONT=lucida console]       description: VGA compatible controller[/FONT]
[FONT=lucida console]       product: Advanced Micro Devices, Inc. [AMD/ATI][/FONT]
[FONT=lucida console]       vendor: Advanced Micro Devices, Inc. [AMD/ATI][/FONT]
[FONT=lucida console]       physical id: 0[/FONT]
[FONT=lucida console]       bus info: pci@0000:08:00.0[/FONT]
[FONT=lucida console]       logical name: /dev/fb0[/FONT]
[FONT=lucida console]       version: c1[/FONT]
[FONT=lucida console]       width: 64 bits[/FONT]
[FONT=lucida console]       clock: 33MHz[/FONT]
[FONT=lucida console]       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb[/FONT]
[FONT=lucida console]       configuration: depth=32 driver=amdgpu latency=0 resolution=1920,1080[/FONT]
[FONT=lucida console]       resources: irq:57 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fc900000-fc9fffff memory:c0000-dffff[/FONT]

---

