---
title: "How do I compile feisty radeon driver for use in gutsy"
date: 2007-10-19
forum: General Help
---

### Post by garymansell on 2007-10-19
Hi,

I have a HP Pavillion ZD8000 laptop with an X600 graphics card which is partially/completely knackered but I used to be able to run Ubuntu Feisty perfectly fine in a non accelerated mode (perhaps it was a low mode that did not even touch the X600 chip?).

I think that it was the combination of the radeon (not ati binary driver) and hashing out the DRI option that allowed the graphics to work in Feisty. I could get a 1440x900x24bpp (Widescreen) video mode that worked OK.

Unfortunately since I have upgraded to gutsy, this same xorg.conf and the new gutsy radeon driver does not work. The new radeon driver seems to trigger a freeze of my machine with the only fix a power reset !!

I have downloaded the source package for the feisty radeon driver - how do I compile it so that I can use it as a replacement driver for my gutsy install (is this even possible?)

I am currently writing this on the machine with the vesa driver and 1024x768 but it's horrible quality when the screen should be presenting 1440x900 sharp and crisp. Is there someway that I can get back to the proper resolution (not bothered about acceleration)

Any help gladly received

Regards

Gary

---

