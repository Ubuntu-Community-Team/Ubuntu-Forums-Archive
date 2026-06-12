---
title: "Gutsy: How to change graphics driver config in text mode"
date: 2007-10-19
forum: General Help
---

### Post by garymansell on 2007-10-19
Hi

I have a HP Pavillion ZD8000 laptop with a knackered ATI X600 graphics card. It would work fine in feisty using the radeon driver and hashing out the DRI line in the xorg.conf file (presumably it is only the 3D part of the gfx chip which is knackered). What would happen is that when the DRI interface to the gfx card is used the machine instantly freezes and crashes. But this was not a problem to me as long as DRI was not used nor the ati binary driver.

I have upgraded to gutsy and the machine boots sucessfully but gutsy seems to have detected the ati driver and selected it. When the graphics switch to a certain mode at boot time my laptop freezes up and crashes my machine. 

I would like to know how to manually change the gfx driver selection in text mode - I can only boot recovery mode as the graphical mode currently configured causes the machine to crash. It used to be the /etc/X11/xorg.conf file but this does not seem to have any effect in gutsy????

What I want to do is (in text mode) configure X to use the radeon driver (does it still exist) and prevent DRI - how do I do this....

Any advice glady received

Thanks in advance

Gary

---

