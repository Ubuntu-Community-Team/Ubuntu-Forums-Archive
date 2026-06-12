---
title: "Nvidia 8800 GT = Unknown device"
date: 2008-06-23
forum: General Help
---

### Post by macaholic on 2008-06-23
I just installed an nvidia 8800 GT, and the drivers are working, however lspci lists the device as ```
08:00.0 VGA compatible controller: nVidia Corporation Unknown device 0602 (rev a2)

```
This is causing complications with software like nvclock, so I would really like to get this resolved, not to mention that it's unsettling to know that ubuntu doesn't fully recognize my card.
NOTE: I have already tried to update the pciids, and after a restart, it's still not recognized.
Update: The 8800 Gt is listed in the pci.ids database, but not udner the same number as mine, 0692 (mine) vs 0611. Please help!

---

### Post by macaholic on 2008-06-23
It appears that they just have not added this card to the database yet, despite there being two submissions for it pending, oh well, I guess I'll just have to wait.

---

### Post by macaholic on 2008-06-23
Well I edited the pci.ids file myself and now it's showing up so, I guess I'm fine now.

---

