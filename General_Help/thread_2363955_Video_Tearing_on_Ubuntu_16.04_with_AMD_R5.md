---
title: "Video Tearing on Ubuntu 16.04 with AMD R5"
date: 2017-06-16
forum: General Help
---

### Post by coreolis14 on 2017-06-16
Hello, I'm a new user on linux, former windows user. I've been using Ubuntu for the last two months and fell completely in love with the OS. 
But lately i've found what appears to be a video tearing issue while watching Netflix, or Youtube on Chrome and Firefox. It's a slight tearing, the image in the video appears to break into wide horizontal lines while playing fast scenes or effects and I seem to get a similar problem while scrolling fast on almost any page. While playing  a video on VLC the problem seems to dim quite a lot, but it is still noticeable.

I'm running Ubuntu 16.04 LTS on an Acer Aspire E15 laptop with  AMD A8-6410 APU with AMD Radeon R5 Graphics  
I'm also aware that ubuntu uses Gallium 0.4 Open source driver on AMD
   lshw -c display  gives this information:

description: VGA compatible controller
       product: Mullins [Radeon R4/R5 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:41 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:4000(size=256) memory:f0d00000-f0d3ffff memory:c0000-dffff


I've already tried [this]("https://cubethethird.wordpress.com/2016/06/14/eliminate-screen-tearing-with-amd-gpu-on-ubuntu/"), but, apparently, it doesn't fix the problem.

Does anyone know or can give me any ideas on how to fix this? I'd apreciate any tip you can give me.
Thanks for reading this!! :)

---

