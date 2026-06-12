---
title: "changed Login Theme...BUT still flashes original color before loading Desktop?"
date: 2008-05-27
forum: General Help
---

### Post by davidkyn on 2008-05-27
changed Login Theme...BUT still flashes original color before loading Desktop? Anyone overcome this? Looks terrible!

---

### Post by OliverW on 2008-05-27
> **davidkyn said:**
> changed Login Theme...BUT still flashes original color before loading Desktop? Anyone overcome this? Looks terrible!

Change the background color in System > Administration > Login Window > Local :) 

If that doesn't work (it only works since Hardy for me), have a look at /etc/gdm/gdm.conf and especially:
BackgroundColor=
GraphicalThemedColor=

Good luck :)

---

### Post by davidkyn on 2008-05-27
Thanks man,
That was really bugging me...cheers:guitar:

---

