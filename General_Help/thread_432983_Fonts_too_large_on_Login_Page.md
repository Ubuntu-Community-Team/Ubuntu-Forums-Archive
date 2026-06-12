---
title: "Fonts too large on Login Page"
date: 2007-05-04
forum: General Help
---

### Post by yarrowfish on 2007-05-04
Hi!

The fonts used on the login page are too large. It became that when I installed the Nvidia drivers. Does anyone now if it's possible to change the font size on the login page? 

I'm running Ubuntu Feisty.

yarrofish

---

### Post by fearevilleet on 2007-05-04
I am having a simular issue, expect my fonts are too small. I have been trying to get this issues fixed since I installed Fiesty. If you figure out how to change the system fonts please post it here.

---

### Post by ayoli on 2007-05-04
Changes due to proprietary drivers could be due due to a screen resolution change.
you can try to edit your theme file which is located under:
```
/usr/share/gdm/themes/<theme_name>/<theme_name>.xml
```
you need to sudo to edit these files
juste find where the fonts are invoked and change size.

---

