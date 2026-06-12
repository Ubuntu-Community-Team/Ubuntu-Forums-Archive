---
title: "rather odd problem i caused"
date: 2006-11-08
forum: General Help
---

### Post by hobieone on 2006-11-08
i transfered some file from my windows drive to my ubuntu drive. now wheni went back into ubuntu the file i transfered to my home folder.  but i cant delete them you any thing it seems due to  they belong to rootuser. now i know you can't log into root so is ther another way i can remove these files  or change thier owner ship?

---

### Post by taurus on 2006-11-08
```
sudo rm <filename>
```

---

### Post by Atomic Dog on 2006-11-09
You also could open a terminal window and type
```
sudo nautilus
```
Then delete the file using the file manager(which acts/works as root).  RM can be such a dangerous command!

---

### Post by CatKiller on 2006-11-09
You should use **gksudo** for graphical applications.

```
sudo chown hobieone:hobieone <filename>
``` will change the owner of the files to the user called **hobieone**.

---

