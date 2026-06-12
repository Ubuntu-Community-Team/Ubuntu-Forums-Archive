---
title: "fixing WINE looks"
date: 2007-08-25
forum: General Help
---

### Post by vexorian on 2007-08-25
I updated WINE to 0.9.44 in hopes it got fixed a bug that affected me (it didn't) the thing is that now everything looks ugly, terribly ugly, the default interface text is set to a gray tone and an ugly font, I tried winecfg to fix it, but it allows me to change everything but that font, this is quite tragic.

It is not a font rendering issue since I was able to use a good font for the menus and they don't suffer from this issue, anyone knows of a registry key or config file I should touch to change the default font?

---

### Post by Qrk on 2007-08-25
The font problem is probably because you don't have ms fonts installed in your virtual windows drive. Windows programs look for a font, don't see one, and use that ugly default. You can fix 90% of font issues by installing the font, download arial32 here:

[http://sourceforge.net/project/downloading.php?group_id=34153&use_mirror=easynews&filename=arial32.exe&18589745](http://sourceforge.net/project/downloading.php?group_id=34153&use_mirror=easynews&filename=arial32.exe&18589745)

and install it with wine.

---

### Post by vexorian on 2007-08-25
It was all working fine until this update even the WINE dialogs have this issue which makes me think it is not related to an ap. (Edit: thanks for attempting to help)

---

### Post by vexorian on 2007-08-29
I am sorry for my latest post, since the fonts did fix the issue. Thanks.

Although it is odd that I never had the fonts and this used to work well.

---

