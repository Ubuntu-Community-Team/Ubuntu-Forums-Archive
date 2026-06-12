---
title: "A weird Graphical glitch when starting Ubuntu 7.10 on Live CD with visual effects on."
date: 2008-01-23
forum: General Help
---

### Post by Sonic6876 on 2008-01-23
Ok, I have a live Cd of Gusty Gibbon and whenever i get into it I get a very weird grpahics glitch. This ONly appears when the visual effects are on,  everything is normal when no visual effects are on. I have an ATI RADEON 128mb videocard. I'm not sure if the videocard is the problem or my 19in widescreen display does anything. I would like to install Ubuntu, but i dont want to take the risk of installing it and gtting the weird graphics glitch. any help will be great.

---

### Post by pointone on 2008-01-23
Please describe this graphics glitch.

---

### Post by geirha on 2008-01-23
I have an ati radeon 9800se and have the same problem. When compiz (the visual effects) are enabled, there are lots of [small red dots](http://launchpadlibrarian.net/10365182/normal.png) on the screen. This is because of the open source ati driver. [quote=http://en.wikipedia.org/wiki/Radeon]The efforts to provide free drivers for these cards continue, though. While the R100 and R200-series chipset drivers were written using specifications provided by ATI (r200 driver), the R300 and R400 series hardware acceleration was written through reverse engineering (r300 driver) the methods used by ATI's proprietary driver. The reverse-engineered code is now in X.Org and Mesa, bringing experimental support for some of the current Radeon cards.[/quote]
My card has an R350 chipset, so obviously the r300 driver isn't quite right yet. Run this in a terminal to see what chipset your card has ```
sudo lshw -class display
```

The [proprietary driver](https://help.ubuntu.com/community/RestrictedDrivers/ATI) should work fine though, but you'll need to use [xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) to get the visual effects. Hopefully there'll be a working open source driver for our cards soon too.

---

### Post by Sonic6876 on 2008-01-23
ok, here is what the glitch looks like.
I' just wondering if this will be fixed if i just cleanly install it...

---

### Post by Sonic6876 on 2008-01-23
> **geirha said:**
> I have an ati radeon 9800se and have the same problem. When compiz (the visual effects) are enabled, there are lots of [small red dots](http://launchpadlibrarian.net/10365182/normal.png) on the screen. This is because of the open source ati driver. 
My card has an R350 chipset, so obviously the r300 driver isn't quite right yet. Run this in a terminal to see what chipset your card has ```
sudo lshw -class display
```

The [proprietary driver](https://help.ubuntu.com/community/RestrictedDrivers/ATI) should work fine though, but you'll need to use [xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) to get the visual effects. Hopefully there'll be a working open source driver for our cards soon too.
here is what i get when i put in the code
```
ubuntu@ubuntu:~$ sudo lshw -class display
  *-display:0             
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 [Radeon X300SE]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0

```

---

### Post by Sonic6876 on 2008-01-23
and i just realized, in the restricted drivers, there is a video driver not in use, and it says it is for the 3D effects. i wonder without it that is what is giving the weird glitch. I may find out when i install Ubuntu.

---

