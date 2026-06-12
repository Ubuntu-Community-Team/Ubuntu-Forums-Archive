---
title: "How do I put a trash icon on Kubuntu desktop?"
date: 2007-04-28
forum: General Help
---

### Post by Athanasius on 2007-04-28
The title of the post says it all.  I am trying to get used to KDE and I cannot figure out how it is done.

---

### Post by aysiu on 2007-04-29
Try this:
[How to Add the Trash Can to Your Kubuntu Desktop](http://linuxfud.wordpress.com/2006/09/24/how-to-add-the-trash-can-to-your-kubuntu-desktop/)

---

### Post by stivani on 2007-04-29
Type this command in a konsole window:
```
cp /usr/share/apps/kdesktop/unused/directory.trash ~/Desktop
```

---

### Post by fredscripts on 2007-08-30
I was wondering the same question, Thanks!!

By the way, how can I surf to the "trash directory?" (I mean something like cd /.../trash) with the Konsole? That will be useful if the X system gets crashed and I wanted to empty the trash.


Thanks!

---

### Post by kuja on 2007-08-30
I'm pretty sure the files are kept in ~/.local/share/Trash/files, however, using Konqueror's trash:/ KIO slave is a bit more elegant.

---

