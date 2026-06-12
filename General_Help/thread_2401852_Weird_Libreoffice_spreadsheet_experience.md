---
title: "Weird Libreoffice spreadsheet experience"
date: 2018-09-23
forum: General Help
---

### Post by raphaell2 on 2018-09-23
A few days ago, I opened an already existing .ods spreadsheet file in Libreoffice, *added* a few values to one column, and saved it. I didn't remove anything. And then I saw that the newly saved version was a bit *smaller* than the previous version. I'm not complaining - none of this caused any problems or trouble for me - but I still find it a bit weird. Any ideas or explanations?

---

### Post by Holger_Gehrke on 2018-09-23
Sure. All OpenDocument files are actually zip-archives full of xml. So the stuff you added changed the contents in such a way that it compressed better. Nothing unusual about that.

Holger

---

### Post by raphaell2 on 2018-09-23
Ah, thank you, that explains it!

---

