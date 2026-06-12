---
title: "strange behavior when dragging/moving windows"
date: 2014-11-17
forum: General Help
---

### Post by soldavi on 2014-11-17
Hello,
I recently installed the latest version of lubuntu on an old acer aspire ZA3 laptop.
Everything seems to be working fine except for when I'm dragging and moving windows around on the desktop.
It's like the window can't keep up with the mouse pointer when it accelerates and lags behind very noticebly. 
Then it keeps on moving for a while even after I've stopped moving the mouse.

I have tried but couldn't find a solution on my own, has anyone experienced something similar?
I'm quite new to linux in general and especially lubuntu but hope to be able to solve it with your help : )

---

### Post by flaymond on 2014-11-17
It happen to me too. I'm a lubuntu user. It happen to me after several hours of installing lubuntu. But, the problems fixed (somehow) when you reboot and after that....it will not happen again (not everytime...because lubuntu is a lightweight flavour...maybe the engine is too fast for an old pc).

---

### Post by soldavi on 2014-11-17
Thanks for the quick reply, but the problem unfortunately still remains after a couple of reboots.

---

### Post by ajgreeny on 2014-11-17
What graphics card/chip have you got on the acer aspire ZA3 laptop.

That is the most likely cause of the problem.

---

### Post by soldavi on 2014-11-18
[FONT=times new roman]Not sure what the exact name is but [SIZE=2][COLOR=#333333]running [/COLOR][/SIZE][/FONT]lspci | grep VGA[COLOR=#333333][FONT=UbuntuRegular] [FONT=times new roman][SIZE=2]gives me 
[/SIZE][/FONT][/FONT][/COLOR]00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
[COLOR=#333333][FONT=UbuntuRegular][FONT=times new roman]
and[/FONT] sudo lshw -C video [FONT=times new roman]gives[/FONT][/FONT][/COLOR]
*-display               
       description: VGA compatible controller
       product: System Controller Hub (SCH Poulsbo) Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=gma500 latency=0
       resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:b0000000-b003ffff

---

