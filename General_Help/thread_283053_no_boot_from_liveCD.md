---
title: "no boot from liveCD"
date: 2006-10-23
forum: General Help
---

### Post by jedrzej on 2006-10-23
Well, I have this brand new system and I tried to boot Ubuntu Live on it. And it doesn't work. It hangs on "mounting root filesystem". What could be the cause? And I would like to add, that Knoppix 4 does not boot either.

My specs:
Intel Core 2 Duo
1GB of RAM
Asus P5B motherboard
Seagate SATA hard drive
another seagate ATA hard drive in slave mode
with a Pioneer DVR-111D drive as its master.
Well, that's the gist of it.

---

### Post by Kateikyoushi on 2006-10-23
I think it is your ata controller.
Which ubuntu version are you trying to install ?

You can try this might help.
Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

