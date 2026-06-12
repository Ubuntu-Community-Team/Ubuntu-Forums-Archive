---
title: "trash"
date: 2008-06-19
forum: General Help
---

### Post by PeterRedford on 2008-06-19
I cant empty my trash can.

anytime I try it just says 

Error removing file: Read-only file system

then asks me to skip or skip all.

which is kinda a pain because well I only have 1 gig free right now.

---

### Post by Dynaflow on 2008-06-19
Open a terminal and type, 

```
sudo nautilus
```

Go to the trash folder in the sidebar, and you should be able to delete whatever is giving the trashcan indigestion.

---

### Post by Dynaflow on 2008-06-19
Actually, nautilus, at least on my computer, seems to exhibit bizarre behavior reminiscent of [GIR from *Invader Zim*]("http://en.wikipedia.org/wiki/GIR_(Invader_Zim)") when the Trash sidebar icon is clicked.

If you get something similar, use nautilus to navigate to /home/YOURNAMEHERE/.local/share/trash/files and delete whatever offends thine eye.

---

