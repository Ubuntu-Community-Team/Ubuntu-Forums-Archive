---
title: "Epson Stylus C60 going crazy"
date: 2007-05-12
forum: General Help
---

### Post by strabes on 2007-05-12
Alright, I don't know if this printer is broken or what, but it is going nuts and I can't figure it out. It's attached locally via USB. I have added it using the kdeprint utility. When I print a test page, it takes a page and sends it all the way though the printer without printing anything on it. It then proceeds to do the same thing with the next sheet and the next sheet ad infinitum. The printer cartridges are brand new, I just put them in there about 5 minutes ago. This is nuts.

---

### Post by cotcot on 2007-05-12
Have you installed the c60 driver ? There is an rpm and install instruction [here]("http://www.avasys.jp/english/linux_e/dl_ink.html").
You have to convert the rpm in deb using alien. After this you should find the printer in cups.

---

### Post by strabes on 2007-05-12
After trying to go through all that nonsense, I found out from [this page](http://ubuntuforums.org/showthread.php?t=436777&highlight=epson+printer) that I could just go to the cups config page in firefox at [http://localhost:631](http://localhost:631) and add it there. Everything works perfectly now.  I am extrremely happy right now. I had this printer sitting in my basement closet for at least a year thinking that it was broken and now it works perfectly. Thank you ubuntu!!!

---

