---
title: "Lubuntu 21.04 color white is using high value"
date: 2021-06-12
forum: General Help
---

### Post by aug7744 on 2021-06-12
Using Lubuntu 21.04 64 bits and Nvidia drivers 465.27.
Nvidia control panel color and some settings all in default with not programs in background changing color temperature or others values.
The problem is any program output areas with white in high value.
See the screenshots below

[ATTACH=CONFIG]288644[/ATTACH][ATTACH=CONFIG]288645[/ATTACH]

How fix it ?
In nvidia control panel changing constrast and gama values not fix that issue.
That issue also happen with video playback and other softwares.

Thanks for your reply.

---

### Post by MAFoElffen on 2021-06-14
Black and white are not necessarily colors.... which are mixtures of red-blue green (RGB).

In NVidia Control Panel > Display > Actual Desktop Color Settings,... The only setting that affects "white" is brightness. The default is 50% 

If setting that is still too bright... I would suspect that the display menu's brightness may need to be adjusted to soften that up also. (A combination of the two).

---

### Post by aug7744 on 2021-06-26
Thanks for your reply.
Even changing values or using default value in Nvidia control panel the problem with white color continues.

---

### Post by him610 on 2021-06-27
Is this on a laptop, or a desktop with connected monitor? What make, model of monitor?
There are different approaches one can use if using a desktop with connected monitor. I have one monitor that was too bright which I finally addressed using *xgamma* from a terminal.
```

inxi -SMCGxz
lshw -c video -sanitize

```
Please show results between code tags.

---

### Post by aug7744 on 2021-09-09
Thanks for your reply.
Desktop LG E1641 using VGA cable.

  *-display                 
       description: VGA compatible controller
       product: GK208 [GeForce GT 640 Rev. 2]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:28 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:fa000000-fbffffff ioport:d800(size=128) memory:c0000-dffff


The problem not is realted with changing settings in nvidia control panel or bright settings.
Is how if a color space or other thing changing the gamma in white color.
Using the binary driver. Nouveau disabled.

---

### Post by aug7744 on 2021-09-11
Please see the link below with screenshots.
Tested 20.04.3 with nouveau because not nvidia drives was released for  20.04.3 in moment , but in 21.04 using nouveau also happen that problem.
20.04.3 happen that problem with white color, but much less than 21.04.

[https://forums.developer.nvidia.com/t/color-white-is-using-high-value-bright-or-gamma/189004/4](https://forums.developer.nvidia.com/t/color-white-is-using-high-value-bright-or-gamma/189004/4)

---

