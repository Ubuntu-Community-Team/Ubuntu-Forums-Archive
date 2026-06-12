---
title: "Ethernet not connecting 14.04lts"
date: 2016-03-21
forum: General Help
---

### Post by jesse49 on 2016-03-21
Hi. Ive just clean installed ubuntu onto my pc and on startup the ethernet tries to connect and never connects.

---

### Post by X-RED_Tech on 2016-03-21
Hi, 

was it connecting before?

---

### Post by jesse49 on 2016-03-21
not since i bought my new motherboard and processor, i have a gigabyte ga-970 gaming board and fx 8320e processor, im assuming it is the killer ethernet that is causing the issue because it had no issue connecting with windows.

---

### Post by X-RED_Tech on 2016-03-21
You probably need to edit GRUB and add "iommu=soft".

---

### Post by jesse49 on 2016-03-21
> **X-RED_Tech said:**
> You probably need to edit GRUB and add "iommu=soft".

ok one moment let me try and do that quickly

---

### Post by jesse49 on 2016-03-22
wow thanks, that helped almost instantly, cant believe that took me over 3 hours to figure out

---

### Post by X-RED_Tech on 2016-03-22
It took me DAYS to figure it out some months ago...

---

