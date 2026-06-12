---
title: "AMD GPU Installation"
date: 2020-09-14
forum: General Help
---

### Post by Lord-Nicon on 2020-09-14
Hello Everyone,

I have a laptop with an old AMD GPU which I want to install the proprietary drivers since the Ubuntu by default drivers doesn't seem to work, I'm using the last LTS version of Ubuntu 
and since there are many drivers to download I don't know which one to install considering the age of the GPU, this are the details of the GPU,

[HTML]
*-display                 
       descripción: Display controller
       producto: Venus XT [Radeon HD 8870M / R9 M270X/M370X]
       fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
       id físico: 0
       información del bus: pci@0000:01:00.0
       versión: 00
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm pciexpress msi bus_master cap_list rom
       configuración: driver=radeon latency=0
       recursos: irq:35 memoria:e0000000-efffffff memoria:f7d00000-f7d3ffff iopo
[/HTML]

If anyone can point me to the correct driver to download , thank you.

---

### Post by QIII on 2020-09-14
There are no drivers to download.  Don't try.  The old ones one could once download do not work with modern Linux distributions.  If you could coax one to install, you'd likely be left needing to re-install a non-operational OS.

At install time, Ubuntu chooses either the open-source radeon driver or the open source amdgpu module depending on which supports your hardware.  Yours appear to be using the radeon driver, which means that is the one that supports your hardware.

What about your driver module does not seem to work?

---

### Post by Lord-Nicon on 2020-09-14
Thank you for answer, even though almost everything seems to work fine with the Intel GPU, I wanted to try some old games which need a dedicated GPU, I have tried installing from Steam and try running the game with the option "Use seconday GPU" that
comes in Ubuntu but they still run really slow, My guess is they are still using the Intel GPU since I don't have the same problem in Windows.

---

### Post by mastablasta on 2020-09-15
you need to manually switch the card using prime command (DRI_PRIME=1):
read more here (Arch Linux is a different distribution but their docs are often very good):
[https://wiki.archlinux.org/index.php/PRIME#Open_Source_Drivers](https://wiki.archlinux.org/index.php/PRIME#Open_Source_Drivers)

or here for Ubuntu example of intel + newer opensource AMDGPU driver (you will use older radeon driver): [https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04](https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04)

one last thing if you want to you can add latest opensource radeon driver using Oibaff PPA. but it might not improve performance for your chip. you would have to check changelogs for that (to see if any improvement was added).
PPA: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

even with PPA you still need to switch manually (just add the command before the game launcher).

---

### Post by Yellow Pasque on 2020-09-16
> **Lord-Nicon said:**
> but they still run really slow, My guess is they are still using the Intel GPU since I don't have the same problem in Windows.

I've seen plenty of complaints of poor performance on the discrete GPU with Intel/AMD hybrid graphics, even if DRI_PRIME=1 is working correctly. Unfortunately, I have not seen a good solution.

---

### Post by mastablasta on 2020-09-16
the only thing is that performance is getting better with time as they improve the driver. might never be as good as in windows, but if it gets close... on xorg site you can see what things are still missing and what things are already done. : [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

for newer chips updates are stil being made. if same issue is resolved for older chips the solutions are backported. but these newish chips have higher chance of getting improvements.

---

