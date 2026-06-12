---
title: "youtube full screen"
date: 2015-01-25
forum: General Help
---

### Post by Bubbelgum on 2015-01-25
I cant play youtube or flash base stream in fullscreen, when i try vidoe stops but sound contineus. i have checked and flash is installed on my system. what can i do ?

---

### Post by mörgæs on 2015-01-25
Sounds like your graphics card is not strong enough. Please post the output from ```
sudo lshw -C video
``` in CODE tags.

---

### Post by Bubbelgum on 2015-01-25
It shoulde be strong enouge, 

```
 
       *-display               
       beskrivning: VGA compatible controller
       produkt: Barts XT [Radeon HD 6870]
       tillverkare: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       bredd: 64 bits
       klocka: 33MHz
       förmågor: pm pciexpress msi vga_controller bus_master cap_list rom
       konfiguration: driver=radeon latency=0
       resurser: irq:48 memory:e0000000-efffffff memory:f7e20000-f7e3ffff ioport:e000(storlek=256) memory:f7e00000-f7e1ffff


```

---

### Post by mörgæs on 2015-01-25
Yes, it's fine hardware. 
Have you checked if closed-source drivers are available?

---

### Post by Bubbelgum on 2015-01-25
i made a screenshot here, but apperently gimp only saves in it&#347; own format.

[http://www.selftest.se/graffedriver.xcf](http://www.selftest.se/graffedriver.xcf)

this is what it says under the driver tab, and those chooses i have. hope u understand this since part of the text is in swedish

---

### Post by coffeecat on 2015-01-25
> **Bubbelgum said:**
> i made a screenshot here, but apperently gimp only saves in it&#347; own format.

Use File -> Export in GIMP and you can then save in png or jpg format (or others) to be able to attach an image as a thumbnail in your post.

You can also create png screenshots in Ubuntu with the PrintScreen key. Add Alt for screenshot of open window.

---

