---
title: "Ubuntu 14.04, removable media keeps auto-mounting after safe removal"
date: 2014-04-21
forum: General Help
---

### Post by I.Bun.Tu on 2014-04-21
I just installed Ubuntu 14.04 on a system with the following specs:

[COLOR=#000000]Corsair Vengeance Pro (2x4GB) ddr3 1600mhz cl9 dimms[/COLOR]
[COLOR=#000000]AMD X6 FX-6300 (6 core, 3.5ghz, 8mb cache)[/COLOR]
[COLOR=#000000]Gigabyte GA-970A-D3P AM3 socket mobo[/COLOR]
[COLOR=#000000]Sapphire Radeon R7 260X OC 2gb, 1150mhz clock, 6600mhz memory
[/COLOR]
and when I try to safely remove my external hard drives they automatically mount again after about 10 seconds. If I just unmount the drive it stays unmounted. 

I have tried a reinstallation on this machine.

I have Ubuntu 14.04 installed on my ASUS G55VW laptop and using the same external hard drives the safely remove option works fine without automatically remounting.

How should I go about troubleshooting this issue? Thanks.

---

### Post by I.Bun.Tu on 2014-04-26
This issue along with a bunch of others was caused by a controller (at least iommu) issue with the AMD 970 chipset on the north bridge of certain motherboards, most notably gigabyte models. I have upgraded to a motherboard with an AMD 990FX chipset and it has solved all of my issues.

---

