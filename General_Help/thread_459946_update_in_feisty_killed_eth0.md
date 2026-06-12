---
title: "update in feisty killed eth0"
date: 2007-05-31
forum: General Help
---

### Post by fredrik_human on 2007-05-31
Hi, I have an networkrelated problem.

I updated Feisty because it said it had updates to install for my system and after reboot, no connetction to network. The lights on my NIC are red/orange and an ifconfig tells me "interrupt: 18 Base address:0x8000" the rest looks fine. I'm using static address. 

My best guess is that the device drivers where screwed up on update but cannot remember if there where any specifik updates for the network drivers, and i do not now how to fix it if that turns out to be the case.

Anyone know what i should do?

---

### Post by zvacet on 2007-05-31
Try to configure your network again.That is best I can think of right now.

---

### Post by fredrik_human on 2007-05-31
well, that's done, over and over again, through GUI and via ifconfig and with no success. i've had a look around the system and here's what is says:

- lsmod returns "8139cp" and "8139too" so apperently the driver modules is loaded into memory ?
- lspci shows the device which proves it to be recognized by the system ?
- There are several alias'es in modules.alias and the device is present in modules.pcimap
- The linklight on the ethernet interface is static red on one side and flashing red on the other.
- I've tried every single cat5 cable i have and bypassed routers and switches with no succes so i don't think it is the cabling or external devices.
- I can ping localhost but that's it.

I'm thinking i might have to reinstall the driver but i'm not shure. 

Regards Fredrik.

---

