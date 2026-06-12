---
title: "ubuntu update overwrites config changes?"
date: 2005-06-10
forum: General Help
---

### Post by inmate on 2005-06-10
good morning,

i install ubuntu not to long back, and had a problem with an irq clash around the sound device. in order to resolve it, i had to add one or two kernel parameters and then all was well.

yesterday, however, i noticed that ubuntu wanted to update itself - so i played along and let it go through the process.

this morning when i booted up, the old sound issue had returned. i looked at the /boot/grub/menu.lst file and my changes had been nixed!
once i added then again, the system returned to normal.

what gives? does ubuntu updates kill config changes? 
how do i prevent this in future?

help would be appreciated!

---

### Post by felipe on 2005-06-10
grub menu.lst is automatically updated by a convenient script run each time a kernel is installed/updated, so just either:

1) make sure to recheck that file when upgrading a kernel or a related package

or

2) put the relevant part outside the #commented out auto-generated kernel list

---

