---
title: "Problems with new system installation, graphics settings?"
date: 2022-10-31
forum: General Help
---

### Post by daanheuvelbeuk on 2022-10-31
Apologies when posted in the wrong forum. 

I have problems with the installation of Linux on my new system. I think it is caused by my graphics card (NVIDIA RTX 3060 12 GB). At the moment my system runs, I can read and send mail, access my files, play videos and music. But when I start my browser (Firefox) my screen becomes black and my system freezes. I am writing this question on a tablet.  

The first time I installed Ubuntu on this new system I forgot to download third party software (for the NVIDIA card). Firefox worked, but the movies not. So I installed it on that system. This resulted in a system that crashed (my screen became black and my system froze). I reinstalled with third party software selected. But I auto start applications, including Firefox, so each time my system crashed before I could do anything. I reinstalled again, an am now asking what to do. 

(I know you usually post a link to a pastebin page with system information. Sadly I could not find my post where I used this, and find the command to generate this info. So some information of my system, hopefully applicable):
```

me@Alfheimr:~$ sudo lshw -c video
[sudo] password for me: 
  *-display                 
       description: VGA compatible controller
       product: GA104 [GeForce RTX 3060]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:2d:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:72 memory:fb000000-fbffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:f000(size=128) memory:fc000000-fc07ffff
  *-graphics
       product: EFI VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1920,1080


me@Alfheimr:~$ glxinfo -B
name of display: :1
display: :1  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Mesa/X.org (0xffffffff)
    Device: llvmpipe (LLVM 13.0.1, 256 bits) (0xffffffff)
    Version: 22.0.5
    Accelerated: no
    Video memory: 32019MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 4.5
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Mesa/X.org
OpenGL renderer string: llvmpipe (LLVM 13.0.1, 256 bits)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 22.0.5
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.5 (Compatibility Profile) Mesa 22.0.5
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 22.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20


me@Alfheimr:~$ lspci -nn | grep -E 'VGA|Display'
2d:00.0 VGA compatible controller [0300]: NVIDIA Corporation GA104 [GeForce RTX 3060] [10de:2487] (rev a1)

About this computer (from settings -> About)
Hardware model: Micro-Star International Co., Ltd. MS-7C37
Processor: AMD® Ryzen 9 5900x 12-core processor × 24
Graphics: llvmpipe (LLVM 13.0.1, 256 bits)
OS Name: Ubuntu 22.04.1 LTS
```

---

### Post by MAFoElffen on 2022-11-01
Please post the output of
```

sudo apt list nvidia* | grep 'installed'

```

Also... Are you running Xorg X11 or Wayland?

---

