---
title: "Unable to change resolution on 18.04 Bionic Beaver"
date: 2019-07-21
forum: General Help
---

### Post by jyeti on 2019-07-21
I recently got a new computer and installed Ubuntu 18.04 LTS on it. It has an AMD Ryzen 5 3500U with AMD Radeon Vega 8 graphics. However, I am unable to change the resolution of the screen from 800x600.
Output of xrandr:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected primary 800x600+0+0 0mm x 0mm
   800x600       75.00*
```
Output of lshw -C display:
```
*-display UNCLAIMED
       description: VGA compatible controller
       product: Picasso
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: -
       bus info: pci@0000:03:00.0
       version: c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f0000000-f01fffff ioport:f000(size=256) memory:fe700000-fe77ffff
```

---

### Post by Autodave on 2019-07-21
How is the monitor connected to the PC: what cable and adapters?  What output from the PC are you using (VGA, HDMI,?) and what input are you using on the monitor?

---

### Post by jyeti on 2019-07-21
Oh, it's a laptop. Forgot to specify that in the original post. I'm not sure what kind of input or output is used internally.

---

### Post by cruzer001 on 2019-07-21
Hello jyeti

Could you post the output of:
```
uname -r && lscpu | grep Model
```

---

### Post by jyeti on 2019-07-21
Ah, never mind. Before I saw the last post, I was messing around with stuff and changed the GRUB resolution, which turned out to change the actual Ubuntu resolution. To anyone with the same problem, run
```
sudo nano /etc/default/grub
```
and change
```
#GRUB_GFXMODE=640x480
```
to
```
GRUB_GFXMODE=(whatever resolution you want)
```
Thanks!

---

### Post by cruzer001 on 2019-07-21
Nice catch :)

---

