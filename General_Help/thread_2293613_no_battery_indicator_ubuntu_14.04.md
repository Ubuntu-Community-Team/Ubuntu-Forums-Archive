---
title: "no battery indicator ubuntu 14.04"
date: 2015-09-06
forum: General Help
---

### Post by Siyanat on 2015-09-06
I have recently dual booted ubuntu 14.04.03 on my hp pavilion 13 with windows 8.1 . To boot this i have had to set acpi=off without which it is not booting.
However I do not see any battery or charging icon on the tray. My power settings looks like this 
[ATTACH=CONFIG]264274[/ATTACH]



:(

---

### Post by PaulW2U on 2015-09-06
Not sure why you posted in Networking & Wireless, so...

*Thread moved to **General Help**.*

---

### Post by Siyanat on 2015-09-06
My bad , I am struggling with a WiFi issue too so made that mistake. Thank you for moving it.

---

### Post by Siyanat on 2015-09-10
Just to update changing the boot parameters to ```
acpi_osi= 
```      did the trick.

---

