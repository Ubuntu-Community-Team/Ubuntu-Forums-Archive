---
title: "SaveFile? how? pdfcrack"
date: 2007-11-17
forum: General Help
---

### Post by opakedragon on 2007-11-17
pdfcrack's man page states that there is a way to save what youve done so far and start back up where you left off.... but it doesnt say how

```
 -l, --loadState=FILE
              Continue from the state saved in FILENAME.

```

maybe its just because I dont really know a whole lot about linux but I cant find anything on the internet. thank you for your help.

---

### Post by pskasten on 2008-04-06
Looking at the source, it seems that pdfcrack will create a save file automatically if the program ends prematurely.  For example, if you "kill" the process that is running pdfcrack, it seems that a save file will automatically be created.

---

