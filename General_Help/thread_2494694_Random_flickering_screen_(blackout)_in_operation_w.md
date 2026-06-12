---
title: "Random flickering screen (blackout) in operation with dmesg error."
date: 2024-01-24
forum: General Help
---

### Post by maximliu on 2024-01-24
Dear Community,
I have problem with flickering screen issue since 22.04, I just updated to 23.10 the issue still persists.
I have 2 screen attached to my intel nuc, with intel Iris Plus Graphic with following hw info.

 description: VGA compatible controller             product: Iris Plus Graphics 640
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             logical name: /dev/fb0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom fb

The problem is that during operation, my both screen randomly blackout for few seconds and back to normal, it is completely random when and how long the blackout would be.
I did the dmsg, there is consistently following information after each flickering.

[ 2394.441427] i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun
[ 2775.874745] i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun



I updated the kernel to 6.5.0-14 with hope this flickering issue will be fixed.
 
I also disabled Wayland in the /etc/gdm3/custom.conf with WaylandEnable=false

My grub modesitting para. looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.fastboot=1 i915.enable_psr=0 intel_idle.max_cstate=4"

The flickering persists, randomly, when I set the resolution of the screen to 1080 instead of 1440, it flickers less frequently as before but still do.

Any suggestions or way to fix this once for all? Thank you !

MAX

---

