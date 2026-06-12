---
title: "Delete xfce panel entry"
date: 2007-10-03
forum: General Help
---

### Post by Hallvor on 2007-10-03
I`m quite new when it comes to xfce, so be understanding. I installed dvdshrink through Wine. It was added to the xfce menu, but even after uninstalling it through the Wine uninstaller, the dead menu entry still pops up. I *really* want to get rid of it. Solutions, anyone?

---

### Post by Hallvor on 2007-10-04
Found the solution myself. The menu entries in Xubuntu are located in .desktop-files. To find them, just open a terminal and type 

```
locate *.desktop
```

I then found the dvdshrink.desktop files and deleted them from Thunar.

---

