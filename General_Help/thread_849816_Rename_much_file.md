---
title: "Rename much file"
date: 2008-07-04
forum: General Help
---

### Post by gumara on 2008-07-04
How can I rename mush a file in one command. I thing it can use command rename but I don't know how to do like this.


eg.

From
 DSCN0156.JPG
 DSCN0049.JPG
 DSCN0076.JPG
 DSCN0103.JPG
 DSCN0130.JPG
 DSCN0157.JPG

To
 yymmdd-DSCN0156.JPG
 yymmdd-DSCN0049.JPG
 yymmdd-DSCN0076.JPG
 yymmdd-DSCN0103.JPG
 yymmdd-DSCN0130.JPG
 yymmdd-DSCN0157.JPG

Thank a lot

---

### Post by vikramaditya on 2008-07-04
You're talking about "batch" renaming.  Sorry, but I'll have to bump this one as I haven't a clue.

---

### Post by unutbu on 2008-07-04
If you want a GUI, try installing the pyrenamer package.

For a command-line solution:
```

for i in DSCN*.JPG; do mv ${i} ${i/DSCN/080704-DSCN}; done
```

---

### Post by aysiu on 2008-07-04
Another great GUI application for batch-renaming is KRename

---

### Post by vikramaditya on 2008-07-04
Here's another way . . .

[https://help.ubuntu.com/community/Photos/BatchRenaming](https://help.ubuntu.com/community/Photos/BatchRenaming)

---

