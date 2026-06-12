---
title: "i915 modeset"
date: 2013-09-27
forum: General Help
---

### Post by suomalainen on 2013-09-27
Ubunteros,

I have Ubuntu 12.04lts installed on a Panasonic Toughbook CF-29 mk1 with an Intel 82852/82855 GM/GME Graphics Controller.

What will happen if I do the following:

sudo gedit/etc/default/grub

and then edit line 10 to read:

GRUB/CDMLINE_LINUX="915.modeset=1"

and then save and quit gedit and issuing a

sudo update-grub


The idea behind all this being that when the grub boot menu loads all the graphics don't look screwed up....

Will this effect how I watch TV using my usb-t adabter or online video?


Thanks

---

### Post by andreazzz on 2013-09-27
No, this will only affect the way your pc boots, not how the graphics are displayed after booting. DVB-T quality might be affected by signal noise, so place the antenna as close as possible to a window and far from electronic devices.
It is possible to alter the quality on YouTube: click on the gear in the right corner and select a higher number.
Or do you mean that the resolution of your screen is to low (for example 800*600)?

---

### Post by suomalainen on 2013-09-27
I mean that I want GRUB menu to look nice and neat

---

