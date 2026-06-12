---
title: "Can I rename a printer?"
date: 2007-02-07
forum: General Help
---

### Post by gosh on 2007-02-07
Does anyone know how to rename a printer?

I had a Officejet 6110 on my network. It broke down so I replaced it with a HP Photosmart C3180.
In CUPS I only replaced the driver.
But the name of the printer is still Officejet 6110.
Can this be changed?

I use ubuntu edgy.

---

### Post by yopnono on 2007-02-07
sudo gedit /etc/cups/printers.conf

Then restart cups

---

### Post by gosh on 2007-02-07
Thnx! Worked perfectly.

---

