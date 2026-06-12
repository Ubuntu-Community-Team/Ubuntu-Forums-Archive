---
title: "warning in terminal re. gedit"
date: 2013-11-02
forum: General Help
---

### Post by vasa1 on 2013-11-02
If I run gedit from a terminal, I see:```
[05:18 PM] ~ $ gedit
** (gedit:2957): WARNING **: Could not load Gedit repository: Typelib file for namespace 'GtkSource', version '3.0' not found
[05:18 PM] ~ $ 
```
This is with gedit 3.8.3 on Lubuntu 13.10.

gedit runs without any visible issues but is this something I can fix?

I have /usr/share/gtksourceview-3.0 with "styles" and "language-specs" as its subfolders.

---

### Post by Frogs Hair on 2013-11-02
There are a number of packages in Ubuntu synaptic with "Typelib files for package name"  in the description ,but no exact match in Ubuntu anyway. I notice that many are not installed and it might be worth looking there.

---

