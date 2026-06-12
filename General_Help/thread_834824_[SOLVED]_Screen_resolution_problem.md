---
title: "[SOLVED] Screen resolution problem"
date: 2008-06-19
forum: General Help
---

### Post by siebesadeq on 2008-06-19
****Any ideas on how to adjust the screen resolution in Hardy Heron? When I open Hardware drivers in administration it says there are no proprietary drivers on this system, and system info shows the following information about Graphic card (see attachment)

---

### Post by ettercap on 2008-06-19
u need to enable that driver and install neccessary drivers for ur card
try googling for the required driver

---

### Post by overdrank on 2008-06-19
> **siebesadeq said:**
> ****Any ideas on how to adjust the screen resolution in Hardy Heron? When I open Hardware drivers in administration it says there are no proprietary drivers on this system, and system info shows the following information about Graphic card (see attachment)

Hi and you may try and use display settings using the alt, F2 keys and this command ```
gksu displayconfig-gtk
```
Some users have had to hand edit the xorg and change the default depth from 24 to 16 and this has helped.

---

### Post by siebesadeq on 2008-06-19
Thanks for your help.

---

