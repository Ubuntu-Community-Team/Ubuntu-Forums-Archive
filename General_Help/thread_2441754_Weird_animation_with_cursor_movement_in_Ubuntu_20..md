---
title: "Weird animation with cursor movement in Ubuntu 20.04"
date: 2020-04-26
forum: General Help
---

### Post by davy jones on 2020-04-26
I just upgraded to Ubuntu 20.04 and there is a very odd thing that keeps happening when I move my cursor around on the desktop. I'm attaching a picture. This goes away if I disable animations in GNOME Tweaks but doing that makes cursor movement extremely slow and jerky and makes the system unusable. What can I do to fix this?

[ATTACH=CONFIG]285631[/ATTACH]

---

### Post by davy jones on 2020-04-28
Bump.

---

### Post by CelticWarrior on 2020-04-28
Which graphics card and drivers?

---

### Post by davy jones on 2020-04-28
This is the output for sudo lshw -class display

```
*-display                 
       description: VGA compatible controller
       product: Mars [Radeon HD 8730M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:35 memory:a0000000-afffffff memory:c0000000-c003ffff ioport:3000(size=256) memory:c0040000-c005ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:33 memory:c1000000-c13fffff memory:b0000000-bfffffff ioport:4000(size=64) memory:c0000-dffff

```

---

### Post by davy jones on 2020-05-03
Bump

---

### Post by davy jones on 2020-05-07
Bump.

---

### Post by davy jones on 2020-05-11
Is no one addressing such bugs??

---

### Post by sdsurfer on 2020-05-11
1) Bumping repetitively will get you little more than ignored. 2) This is not a bug in Ubuntu; it is something with your graphics or drivers. I have experienced this before in a different scenario.

I am using a Dell docking stating with an old monitor, the only reason for using it is this pandemic has driven me out of my normal office where I have two HMDI BenQ's and am forced to use an old VGA as a second monitor that only has a VGA port. It displayed these symptoms exactly, fortunately all that was required was a hard restart. It was the docking station's issue communicating with the USB port.

I have had other issues on a System76 Gazelle laptop which, in my case, because it has an Nvidia GPU, was using the default Noveau driver. That is not likely your case, but your lshw output tells you what ***drivers*** you are using, are they correct for your hardware?

Once you figure that out, check for updates to the drivers. A seldom checked place when it comes to display is software & updates. Have a look at the Additional Drivers tab, see if anything loads and if you can switch to it.

---

### Post by davy jones on 2020-05-15
I'm just using the default drivers. There's nothing in the Additional Drivers tab in Softwares & Updates.

Also, I didn't face this with 12.04, 14.04 or 18.04 on the same laptop with the same graphics card, which is why I assumed that this is a bug in Ubuntu 20.04. And also because this is the first Ubuntu OS that I've used that supports switchable graphics out of the box. Previously versions that I used only ran on my Intel graphics card.

---

### Post by davy jones on 2020-05-22
Even after updating my driver using the instructions [here]("https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation") under Method 2, the problem hasn't gone away.

---

### Post by davy jones on 2020-05-25
SOLVED: This has nothing to do with the graphics card. This happens if zoom is enabled on desktop. If you switch it off, it'll go away.

---

