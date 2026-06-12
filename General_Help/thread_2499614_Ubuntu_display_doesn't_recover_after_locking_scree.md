---
title: "Ubuntu display doesn't recover after locking screen with HDMI connection"
date: 2024-08-03
forum: General Help
---

### Post by dfeqwfwgrgvxfds on 2024-08-03
Problem:
 When I lock my screen using the OS key + L shortcut while connected  to an external display via HDMI, I can't get the display to show up  again afterwards. The screen remains blank no matter what I do.

 
What I've tried:

 Disconnecting the HDMI cable, Disconnecting and reconnecting the HDMI cable
Waiting for an extended period


 Current workaround:

The only solution I've found is to force restart the system, which is inconvenient and disruptive to my workflow. System details:

 
Operating System: Ubuntu 24.04 LTS (64-bit)

 
Graphics card:


 > sudo lshw -C display

 *-display                 
       description: VGA compatible controller
       product: GA103M [GeForce RTX 3080 Ti Laptop GPU]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=nvidia latency=0 mode=2560x1600 visual=truecolor xres=2560 yres=1600
       resources: iomemory:600-5ff iomemory:640-63f irq:236 memory:6f000000-6fffffff memory:6000000000-63ffffffff memory:6400000000-6401ffffff ioport:5000(size=128) memory:70080000-700fffff
  *-display
       description: VGA compatible controller
       product: Alder Lake-P GT2 [Iris Xe Graphics]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=2560,1600
       resources: iomemory:640-63f iomemory:400-3ff irq:235 memory:642f000000-642fffffff memory:4000000000-400fffffff ioport:6000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff


 
> xrandr | grep " connected"

eDP-1 connected (normal left inverted right x axis y axis) HDMI-1-0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 698mm x 393mm

---

### Post by currentshaft on 2024-08-03
F4

---

### Post by dfeqwfwgrgvxfds on 2024-08-03
I don't want to risk losing my session right now, but I will try on the next unlock.

---

### Post by dfeqwfwgrgvxfds on 2024-08-08
Sorry for the late answer. Yes that actually worked. So sometimes it works, sometimes it doesn't. I updated the drivers using ubuntu-drivers and the screen doesn't show up problem itself is gone. But now, sometimes the builtin laptop screen (not the hdmi one) starts to jitter when I wake up from lock or suspend. Sometimes keyboard and mouse (neither the external ones, nor the laptop builtin ones) have all input ignored when on the unlock screen after waking up from lock or suspend, eliciting no reaction.

---

