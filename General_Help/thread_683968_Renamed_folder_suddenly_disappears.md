---
title: "Renamed folder suddenly disappears?"
date: 2008-01-31
forum: General Help
---

### Post by Sonja on 2008-01-31
I renamed a folder, using a period as the first character, and suddenly the folder disappeared. The folder was not in my trash either! What happened? Halp.

---

### Post by hal736 on 2008-01-31
You created a "hidden" directory.  

If you have a terminal open, you can type* ls -la* and you will see your directory.

If you are using Nautilus, go up to _V_iew at the top of the file browser, and click on* Show Hidden Files*. (or press the CTRL and h keys)  and your directory will magically reappear.

Have fun!

---

### Post by ~LoKe on 2008-01-31
Yep.  In Linux, prefixing a file or folder with a period causes it to be hidden.  This is used for config files and directories in the /home folder.  It's a better system that Microsoft's implementation, because it's much more logical.  But yeah, just press ctrl+h to see hidden files, then remove the period.

---

### Post by Sonja on 2008-02-01
They should add a warning in Nautilus. "Warning: adding a period in the beginning of this file will render it invisible" the first time a user does that! :)

---

### Post by ~LoKe on 2008-02-01
> **Sonja said:**
> They should add a warning in Nautilus. "Warning: adding a period in the beginning of this file will render it invisible" the first time a user does that! :)

Read some of the documentation.  It prevents annoying intrusions like this.

---

### Post by jjross on 2008-02-01
Its really not a big deal if you know about it.
In the file browser go to View and check the "Show Hidden Files" box and they will show up.

---

