---
title: "GRUB doesn't work with multi-GPU"
date: 2016-04-10
forum: General Help
---

### Post by joshua37 on 2016-04-10
The GRUB wont display on my monitor while I'm using my second video card as the main source, which is required as I have a short mainboard and the cards are air-cooled for now.

If I don't physically swap the cable to my first card it seems the GRUB tries lowering the display resolution until it eventually breaks down and displays lines of text.

I would greatly appreciate a better work around than swapping the cables.

---

### Post by QIII on 2016-04-10
It might be helpful if you would provide the details of your machine's hardware specifications and the release of Ubuntu that you are using.

---

### Post by grahammechanical on 2016-04-10
The Grub menu is only on the screen for 10 seconds before Grub will load the default OS in its menu. Video drivers are not activated until partway through loading Linux & loading Ubuntu as a follow on. Linux gets the optimum screen resolution from the monitor's EDID (Extended Display Identification Data) chip. It is Linux that is struggling to set a screen resolution.

Are these two video adapters from the same manufacturer? Do you have a proprietary video driver installed?

Regards.

---

### Post by joshua37 on 2016-04-10
> **grahammechanical said:**
> The Grub menu is only on the screen for 10 seconds before Grub will load the default OS in its menu. Video drivers are not activated until partway through loading Linux & loading Ubuntu as a follow on. Linux gets the optimum screen resolution from the monitor's EDID (Extended Display Identification Data) chip. It is Linux that is struggling to set a screen resolution.

Are these two video adapters from the same manufacturer? Do you have a proprietary video driver installed?

Regards.

Their two GTX 670's from two different manufacturers and yes I'm fairly certain I'm using the proprietary drivers.

---

### Post by cariboo on 2016-04-10
To check what graphics driver you are using, issue the following command:

```
sudo lshw -C display
```

the results should look similar to this:

```
sudo lshw -C display
[sudo] password for cariboo: 
  *-display               
       description: VGA compatible controller
       product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: **driver=i915 **latency=0
       resources: irq:91 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)
```

I've bolded what you should look for.

---

### Post by joshua-c-axisa on 2016-04-12
> **cariboo said:**
> To check what graphics driver you are using, issue the following command:

```
sudo lshw -C display
```

the results should look similar to this:

```
sudo lshw -C display
[sudo] password for cariboo: 
  *-display               
       description: VGA compatible controller
       product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: **driver=i915 **latency=0
       resources: irq:91 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)
```

I've bolded what you should look for.

configuration: driver=nvidia latency=0

EDIT: Also I've realised that its not just the GRUB not working from the second card but Ubuntu as well.

---

