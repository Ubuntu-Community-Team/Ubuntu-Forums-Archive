---
title: "nvidia error"
date: 2019-03-18
forum: General Help
---

### Post by sniper8752 on 2019-03-18
I recently upgraded my ubuntu server from 16 to 18, and now upon boot, I get this error: nouveau unknown chipset
I tried adding the following to my boot menu:

nomodeset nouveau.modeset=0

But it did not recognize nomodeset.

---

### Post by Autodave on 2019-03-19
Upgrading can often cause problems like that.  Can you give us some specs on your machine: especially what video card?  In 16.04, did you install and driver for the video card?  If so, what one and where did you get it from?

---

### Post by sniper8752 on 2019-03-23
The video card is a geforce gtx 1050.  When you say "install", I believe I just pulled anything that was available from the apt repo.

---

### Post by Autodave on 2019-03-23
OK: at least you got the right driver from the right place.  When you boot, how far can you get?  Do you get to the main screen, a terminal, etc?

---

