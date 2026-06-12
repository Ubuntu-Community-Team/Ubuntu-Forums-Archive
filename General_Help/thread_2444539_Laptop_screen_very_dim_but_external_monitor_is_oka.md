---
title: "Laptop screen very dim but external monitor is okay"
date: 2020-05-31
forum: General Help
---

### Post by eaglesky1990 on 2020-05-31
I recently noticed that my laptop screen is very dim and brightness control doesn't work. External monitor connected through HDMI is able to display normally. 

My laptop is Lenovo Y50-70 with both Windows 8.1 and Ubuntu 16.04 LTS installed. On startup the grub menu doesn't show up anymore (with or without external monitor connected), but still able to boot into Ubuntu because that's the default option. There are two graphic cards in the laptop:

```
  *-display               
       description: 3D controller
       product: GM107M [GeForce GTX 860M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:d1000000-d13fffff memory:c0000000-cfffffff ioport:5000(size=64)

```

And I'm using the intel one now. I tried the solution[ here]("https://askubuntu.com/questions/1034305/brightness-problem-ubuntu-18-04-lts") specifying `[COLOR=#242729][FONT=Consolas]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"` but it doesn't make any difference. Also pressed "Alt + F2" to change the backlight, didn't work either. Pressing "Alt + F3" would switch the display options but the laptop screen is always dim. 

I don't know when this issue started to happen, but long time ago both screens were able to display normally. I suspect it might be due to some configuration change I did but I don't remember. Any suggestion on things I could try to fix it?

Thanks. Let me know if you need any more information.[/FONT][/COLOR]

---

