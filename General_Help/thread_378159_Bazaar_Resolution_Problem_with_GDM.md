---
title: "Bazaar Resolution Problem with GDM"
date: 2007-03-06
forum: General Help
---

### Post by BarfBag on 2007-03-06
I'm having a bazaar problem with GDM and resolutions.

My preference is 1024x768.  GDM was at 1280x1024 by default.  To make it start in 1024x768, I edited xorg.conf and made it the first resolution next to "Modes."  Now, it starts at that resolution, but there's a view.  The screen is zoomed in, and to see what's up, down, left, and right I have to push the mouse against the edge in that direction.  I know that sounds weird, but I can't describe it any clearer.

Ubuntu Edgy
nVidia Geforce 5500 FX (256 MB VRam)

---

### Post by po0f on 2007-03-06
BarfBag,

Do you have a "vga=<blar>" kernel parameter set?  This would be the only thing I can think of that could (maybe) affect this.

---

### Post by BarfBag on 2007-03-07
> **po0f said:**
> BarfBag,

Do you have a "vga=<blar>" kernel parameter set?  This would be the only thing I can think of that could (maybe) affect this.

I don't know.  How do I check?

---

