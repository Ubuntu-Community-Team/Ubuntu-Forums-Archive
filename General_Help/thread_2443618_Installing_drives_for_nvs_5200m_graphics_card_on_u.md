---
title: "Installing drives for nvs 5200m graphics card on ubuntu 20.04"
date: 2020-05-18
forum: General Help
---

### Post by noob-at-linux on 2020-05-18
I am trying to install nvidia drivers for my nvs 5200m graphics card and I have failed all the time.
I have tried various ways on various sites but nothing helped.
And when I installed nvidia drivers and opened nvidia settings only thing I can see is  prime profiles.
```
lspci | grep -i VGA  
```
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)


```
```
sudo lshw -c video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GF108GLM [NVS 5200M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
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
       resources: irq:37 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff

```I tried installing recommened packages from software-properties-gtk but still of no use.
I don't know if these outputs will be helpful but I guess it will!
Regards.

---

### Post by wildmanne39 on 2020-05-18
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by Autodave on 2020-05-18
The "M" in your graphic's card name tells me that it is a laptop unit.  Please give us make and model of laptop and specs if you know them.

---

### Post by CelticWarrior on 2020-05-18
NVS5200M needs the 390 driver and thios version only. Trying to install any other will fail.

---

### Post by noob-at-linux on 2020-05-18
It's dell latitude E6430

---

### Post by noob-at-linux on 2020-05-18
Maybe my ubuntu broke because of things I was trying on it so I am reinstalling it. Will install 390 drivers as you stated as soon as I reinstall my ubuntu.

---

### Post by noob-at-linux on 2020-05-18
> **CelticWarrior said:**
> NVS5200M needs the 390 driver and thios version only. Trying to install any other will fail.
I installed 390-drivers before reinstalling ubuntu and restarted the laptop and it worked! Thank you so much. I almost spend a complete day trying to figure it out.

---

