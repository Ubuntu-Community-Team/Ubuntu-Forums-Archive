---
title: "[SOLVED] HP 2360 printer problem"
date: 2007-01-17
forum: General Help
---

### Post by Adaminla on 2007-01-17
Have a HP D2360. CUPS identifies it as a 1000c. How do I install the correct driver. In present CUPS configuration nothing happens when i go to print so I'm thinking that the driver CUPS has chosen is the wrong one. Also how do I get Ubuntu to identify the printer correctly (viz. as a D2360 and not a 1000c)?

---

### Post by LeleJones on 2007-09-18
Do not try to install the printer using CUPS.

Download the HPLIP from sourceforge and follow the installation procedure. It worked well for me.

(Do not forget to choose the HP D2300 series driver during configuration).

---

### Post by defenestratos on 2008-02-14
That worked flawlessly! Thank you

---

