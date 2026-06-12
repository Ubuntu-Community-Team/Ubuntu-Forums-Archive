---
title: "640x480 screen resolution, no other choices available"
date: 2018-01-18
forum: General Help
---

### Post by ken355 on 2018-01-18
I am new to Ubuntu.  I installed Ubuntu 16.04 onto an old Acer Aspire 5000 series laptop.  The screen resolution is fixed at 640x480, with no other options to choose from.  This renders the laptop nearly useless, as most open windows fall off the edge of the screen.  When I first tried out Ubuntu, I ran it from the CD before I installed it.  The resolution was okay then.  However, once I installed it, it reverted to 640x480, but I know this laptop is capable of higher resolutions.  

Supposedly, this PC uses a SiS M760GX video card, which, from what I have read, may be problematic for Ubuntu.  

Here is the Terminal output from "Xrandr":
xrandr: Failed to get size of gamma for output default screen 0: minimum 640 x 480, current 640 x 480, maximum 640x480  
default connected primary 640x480+0+0 0mm x 0mm   
640x480   73.00*

Is there a way to get another display resolution?  I'd like at least 1024x768.

---

### Post by mörgæs on 2018-01-18
Hi, welcome to the fora.

SIS graphics cards are a well-known problem. First please run ```
lshw -C video
``` and post the results in CODE tags.

---

### Post by ken355 on 2018-01-18
Hello,
output from lshw -c video:
* -display UNCLAIMED
description: VGA compatible controller
product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA display adapter
vendor: Silicon Integrated Systems [SiS]
physical id: 0
bus info: pci@ 0000:01:00.0
version: 00
width: 32 bits
clock: 66 MHz
capabilities: pm agp agp-3.0 vga_controller cap_list
configuration: latency=0
resources: memory: e8000000-efffffff
memory: e2100000-e211ffff
ioport: a0000 (size 128)
memory: c0000-dffff

---

### Post by mörgæs on 2018-01-19
Hardware of this age should run Lubuntu and not Ubuntu but even with Lubuntu the resolution is probably low. 
I suggest trying [this approach]("https://ubuntuforums.org/showthread.php?t=2252413&page=3&p=13376449&viewfull=1#post13376449") in which you change 0.10.8 to 0.10.9

Again, please make it a habit to use CODE tags for terminal output.

---

