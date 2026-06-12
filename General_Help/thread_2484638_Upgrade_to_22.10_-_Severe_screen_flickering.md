---
title: "Upgrade to 22.10 - Severe screen flickering"
date: 2023-03-05
forum: General Help
---

### Post by Mr Fredrick on 2023-03-05
Hi All,

I have just upgraded my machine (see signature) from 22.04 to 22.10 which has resulted in severe screen flickering. I've never encountered this problem before. Does anybody know how I can fix this?
Thanks in advance.
MrFred

---

### Post by grahammechanical on 2023-03-05
Ubuntu 22.04 is a Long Term Support (LTS) release. It is supported until April 2027 and is available for a further 5 years support by registering with Ubuntu Pro. Whereas, Ubuntu 22.10 reaches end of life in July 2023. 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Are you using the proprietary Nvidia video driver or the open source video driver? Try changing video drivers.

Regards

---

### Post by Mr Fredrick on 2023-03-05
This is the output I get if I type:
sudo lshw -C display

  *-display                 
       description: VGA compatible controller
       product: TU116 [GeForce GTX 1660]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:83 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
  *-graphics
       product: EFI VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1920,1080

How can I reinstall the nvidia drivers or switch to another driver?
Thanks in advance.

Additional info:
When I go to Additional Drivers in Software Updates all the nvidia options are grayed/greyed out and un-selectable.
The bottom line reads: "No proprietary drivers are in use."

---

### Post by Mr Fredrick on 2023-03-05
I eventually installed nvidia-driver-515, when I restarted everything was OK although I'm not actually using the nvidia driver.

---

