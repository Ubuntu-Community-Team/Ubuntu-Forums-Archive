---
title: "Correct video driver"
date: 2013-07-15
forum: General Help
---

### Post by rmcellig on 2013-07-15
I have  an Acer All In One that is  about three years old. The webcam doesn't seem to work and I have a hunch it is a driver issue. What driver should I use based on this output:


```

  *-display:0             
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fc000000-fc3fffff memory:e0000000-efffffff ioport:1c20(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:f0000000-f00fffff

```

---

### Post by dino99 on 2013-07-16
xserver-xorg-video-intel is what your graphic needs
but the webcam is drived by the kernel: use one of the latest : [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

