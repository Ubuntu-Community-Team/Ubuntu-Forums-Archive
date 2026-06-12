---
title: "AWN on 7.10?"
date: 2007-11-05
forum: General Help
---

### Post by notna01 on 2007-11-05
How do i get it to work? Cause i get this error:
```
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'libwnck-1.0' found


```

---

### Post by experience on 2007-11-05
Maybe you can just try installing the dependent packages with the command:
```
sudo apt-get install glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0
```

---

### Post by notna01 on 2007-11-05
> **experience said:**
> Maybe you can just try installing the dependent packages with the command:
```
sudo apt-get install glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0
```

didnt work.....

---

### Post by zvacet on 2007-11-05
You can get AWN here

[http://www.getdeb.net/search.php?keywords=AWN]("http://www.getdeb.net/search.php?keywords=AWN")

---

### Post by mivo on 2007-11-05
You can also follow the How-To [here]("http://ubuntuforums.org/showthread.php?t=385981"). Make sure you add the right repository. (The 64-bit version you get by following the How-To is more current than the one you get from Getdeb.net right now -- this may or may not apply to the 32-bit version, but I cannot say for certain. There was an update for the 64-bit version via the repository yesterday.)

---

