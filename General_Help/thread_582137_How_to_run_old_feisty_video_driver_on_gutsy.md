---
title: "How to run old feisty video driver on gutsy"
date: 2007-10-19
forum: General Help
---

### Post by garymansell on 2007-10-19
Hi,

I have a HP Pavillion ZD8000 laptop with an X600 graphics card which is partially/completely knackered but I used to be able to use it OK with Ubuntu Feisty in a non accelerated mode.

I think that it was the combination of the radeon (not ati binary driver) and hashing out the DRI option that allowed the graphics to work in Feisty. I could get a 1440x900x24bpp (Widescreen) video mode that worked OK but since I have upgraded to gutsy, this same xorg.conf does not work.

I was wondering if there is any way that I can use the Feisty radeon module for gutsy, or whether there is another way of accessing that same video mode that worked in Feisty.

I am currently writing this on the machine with the vesa driver and 1024x768 but it's horrible quality when the screen should be presenting 1440x900 sharp and crisp.

Any help glady received

Regards

Gary

---

### Post by stream303 on 2008-02-22
I did exactly that with my nv driver on Feisty to fix a bug with Gutsy when all known efforts failed to cure a shifted display (resolution was correct)

The key was to copy the nv_drv.so file from
/usr/lib/xorg/modules/drivers

to the same directory on my Gutsy install.  I just copied it to a usb key, and to make it graphically easy, I just ran

gksudo nautilus

to do the copying.

Maybe you can swap out your ati_drv.so (or whatever it is called) and try that...

---

