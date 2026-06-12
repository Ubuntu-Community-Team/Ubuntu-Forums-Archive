---
title: "genius scanner"
date: 2006-07-07
forum: General Help
---

### Post by xyrer on 2006-07-07
Hi, i managed (after a long time and several tries) to get my genius colorpage-vivid 1200xe scanner working, i jump for happiness until i found out it only scans in b&w, when i put it to scan in color, it starts to make a horrible noice and the picture comes out bad.

Anyone has seen this? i compiled sane and xsane myself, i have the firmware from the cd and followed some instructions i found on the web, i think i did everything right but missed something somewhere, anyone can help please? i want to definitely put my Windows in the trash and forget about it.

---

### Post by zxee on 2006-07-07
Are you using the right backend [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)
Also you may want to check on the relevent SANE page to see if others are experiancing problems or know of a fix.

---

### Post by xyrer on 2006-07-08
Well, it is the right backend, is not a problem with xsane, it happens with kooka too, and it only happens when i do a preview in color, by now, i have to preview in b&w and then scan in color and it works.

---

### Post by zxee on 2006-07-08
> **xyrer said:**
> Well, it is the right backend, is not a problem with xsane, it happens with kooka too, and it only happens when i do a preview in color, by now, i have to preview in b&w and then scan in color and it works.

kooka uses the sane backend. 
The sane scanner supported devices page: [http://www.sane-project.org/cgi-bin/driver.pl?manu=genius&model=&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=genius&model=&bus=any&v=&p=)
lists the status of your model as "good" which means development is not complete and some functions may not work.

---

### Post by xyrer on 2006-07-10
Well, then i'll have to wait. thank you very much.

---

