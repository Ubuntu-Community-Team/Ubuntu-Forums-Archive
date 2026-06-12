---
title: "Sofware center error when opening it in Gnome Remix"
date: 2012-10-20
forum: General Help
---

### Post by javiribera on 2012-10-20
After a Ubuntu 12.10 Gnome Remix fresh install, I installed software-center and when opening it I get this error:

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 128, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 105, in <module>
    from softwarecenter.ui.gtk3.panes.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/installedpane.py", line 35, in <module>
    from softwarecenter.db.categories import (CategoriesParser,
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 30, in <module>
    import lxml.etree as ET
ImportError: /usr/lib/i386-linux-gnu/libexslt.so.0: cabecera ELF inválida
```

and nothing else.

("cabecera ELF inválida" = "invalid ELF header")

Any ideas?
Thanks

---

### Post by raja.genupula on 2012-10-20
try this 

```
sudo apt-get install --reinstall software-center
```

---

### Post by javiribera on 2012-10-20
> **raja.genupula said:**
> try this 

```
sudo apt-get install --reinstall software-center
```

Windows style! Didn't work, but thank you anyway.

---

### Post by raja.genupula on 2012-10-20
you getting the same error ?

---

### Post by javiribera on 2012-10-20
> **raja.genupula said:**
> you getting the same error ?

Yes

---

### Post by javiribera on 2012-10-20
New info:

Similar error when opening nautilus:

```
user@PCHabitacion:~$ nautilus
nautilus: error while loading shared libraries: /usr/lib/i386-linux-gnu/libexif.so.12: invalid ELF header
user@PCHabitacion:~$
```

---

### Post by javiribera on 2012-10-20
Well, I reinstalled and "solved" it. I don't like to fix things this way, hope this is not common in ubuntu...

---

