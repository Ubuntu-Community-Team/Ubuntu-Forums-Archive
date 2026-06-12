---
title: "Help with configuring video cards"
date: 2007-03-06
forum: General Help
---

### Post by colbeyl on 2007-03-06
I recently purchased a GeForce FX5200 (pci) for my outdated Dell 2400 and i desperately want to use Ubuntu again, but the X server refuses to start and I have no experience in configuring it... the integrated video card, which cannot be turned off in the BIOS, is an Intel 82845G. I only have one monitor, which will be on the 5200, and I pretty much just need to know how to configure X so that it works as if the integrated card is not there.

---

### Post by magicfab on 2007-03-06
in a terminal window, the "lspci" command will list all PCI and onboard graphic controllers. In xorg.conf you need to specify the appropriate device ID in the "Device" section under BusID.

Good luck.

---

### Post by tyler_roach on 2007-03-07
Most BIOS's automatically disable the integrated video when you put in a graphics card, so your problem shouldn't be there. What's most likely happening is that X is still using the video drivers for your integrated graphics, which won't work with the new card. To change that, get to a command line and type:

sudo dpkg-reconfigure -phigh xserver-xorg

and choose your video driver (you can use either nvidia or vesa, if I'm not mistaken) and screen resolution from the list, and then every thing should be fine.

---

### Post by tyler_roach on 2007-03-07
> **magicfab said:**
> in a terminal window, the "lspci" command will list all PCI and onboard graphic controllers. In xorg.conf you need to specify the appropriate device ID in the "Device" section under BusID.

Good luck.

Obviously, do that first.

---

