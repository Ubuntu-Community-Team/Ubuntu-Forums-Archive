---
title: "Gutsy ATI Driver issue"
date: 2007-10-21
forum: General Help
---

### Post by foxmulder881 on 2007-10-21
I have just finished upgrading to Gutsy and I am now having problems with my vid card drivers.

Upon reboot, it asks me which driver, resolution etc to select. It doesn't seem to matter which one I choose, it still doesn't seem to work properly.

When I go to System>Restricted Drivers Manager, it says the driver is enabled but not in use.

How do I enable it to use the driver?

A worthy note... on video playback, speech is behind the sound. I suspect it's a related issue.

---

### Post by scott_evil on 2007-10-21
I had the same problem with my AMD/ATI x1600 card.
I installed ENVY and then ran the ATI driver install two times in a row. Now it works.
Restricted driver is not checked, but says In Use now.

- Uncheck the restricted driver.
- Install ENVY.
- Run the ENVY ATI driver install then restart X (reboot).
- Run the ENVY ATI driver install then restart X (reboot).
- Check the driver in the Catalyst Control Center or go to a terminal window and type fglrxinfo.


HTH

---

### Post by foxmulder881 on 2007-10-21
I've tried uninstalling and reinstalling several times over to no avail.

What is ENVY?

The video driver worked perfect in Feisty, what's the go with Gutsy?

---

### Post by MrFurious on 2007-10-23
> **foxmulder881 said:**
> When I go to System>Restricted Drivers Manager, it says the driver is enabled but not in use.

How do I enable it to use the driver?

I had the same problem after I upgraded tonight.  I disabled the driver (which apparently uninstalled fglrx), rebooted, then reenabled the driver.  After a final reboot, I was fixed.

---

### Post by foxmulder881 on 2007-10-24
Nothing I tried seemed to work. So I cracked it and installed a fresh install of Gutsy and it worked perfectly.

I'd say there's a clear and obvious bug with the video drivers after an upgrade.
This was the first time I had performed an upgrade as I usually perform a fresh install.
I think I'll be sticking with the fresh install from now on as this is the primary reason I have avoided upgrades in the past. It always seems to be one problem after another. Somehow, I thought that upgrading from Feisty to Gutsy would be different.

---

