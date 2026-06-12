---
title: "LibreOffice error: Read-Error. Format error discovered in the file in sub-document."
date: 2018-01-06
forum: General Help
---

### Post by ark-i5 on 2018-01-06
I keep getting this error every time I try to open my LibreOffice document: 

Read-Error.
Format error discovered in the file in sub-document content.xml at 2,16950(row,col).

I've unzipped the contents and found the content.xml file but I have no idea how I'm supposed to know what's actually wrong with the code??

Can someone please tell me what the problem is/fix it for me? I've attached the original document.

Thank you.

---

### Post by Holger_Gehrke on 2018-01-06
Same old: an attribute was defined twice for the same tag, in this case a background colour in a style tag.

Holger

---

### Post by ark-i5 on 2018-01-06
Thanks a million man!

---

