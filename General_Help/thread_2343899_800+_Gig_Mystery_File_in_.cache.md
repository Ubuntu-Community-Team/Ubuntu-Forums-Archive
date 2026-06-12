---
title: "800+ Gig Mystery File in .cache"
date: 2016-11-20
forum: General Help
---

### Post by noavbazzer on 2016-11-20
The other day I turned on my laptop to discover I'm out of space. I located the file responsible in the .cache. It's called:

tmpKRXFY1PykUk22xl34KYqD3BghxZN8hY78MF73e44dm_hPpfFiuCVww.G_rIB4D_q2z48SkQDoSZi.fNgoEzjoCKzm-Pd42KqwFzroTeHnytpwDJjEE3R_VJzbseW2_j0M9cjaWrZnm9T9_ope_WBTkFcAiJXZlKtT6ZjUlL2Xum7le2.3aZbcs1CZqL-UJ4Hdj02dryQTXT1W.eMhusRAqC.mpjXTb03ZlcmP4HOhML.z.lNTW6tE1MqlFw

Its just sitting right in the .cache folder and it is 837.7 GB. How do I figure out what is writing this file and how to stop it from happening again?

---

### Post by TheFu on 2016-11-20
Use **lsof**.

---

### Post by noavbazzer on 2016-11-20
When I run lsof by itself the file doesn't seem to be listed and when I run lsof with the file path it returns nothing.

---

### Post by &amp;KyT$0P# on 2016-11-20
Isn't that Bleachbit?  Sounds similar to [this thread]("https://ubuntuforums.org/showthread.php?t=2331523"), anyway.

---

### Post by noavbazzer on 2016-11-20
I believe you are right. I deleted the file, I'll keep an eye out for it popping up again.

---

### Post by TheFu on 2016-11-20
Using lsof isn't hard, once you know how. [https://www.ibm.com/developerworks/aix/library/au-lsof.html](https://www.ibm.com/developerworks/aix/library/au-lsof.html)

---

