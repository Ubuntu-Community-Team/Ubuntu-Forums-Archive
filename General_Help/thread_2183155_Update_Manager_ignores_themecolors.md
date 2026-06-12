---
title: "Update Manager ignores theme/colors"
date: 2013-10-23
forum: General Help
---

### Post by wANGExM on 2013-10-23
In 13.10 Update manager now ignores colors and themes. I thought perhaps they moved to the qt4 toolkit as in the past applications that ignore the user theme/color preferences were using the QT kit but no luck, it simply doesn't give a s#$t what the users color scheme is.

Earlier today some things crashed and the dialogs also ignored the theme / user defined colors. At present I'm using Clear Looks with custom colors and "random" elements in the system ignore my color settings/preferences.

More and more I'm finding things that all ignore my custom theme colors. I'm guessing from what I've found this is a gtk3 issue...I guess I'll downgrade.

---

### Post by vasa1 on 2013-11-02
> **wANGExM said:**
> Earlier today some things crashed and the dialogs also ignored the theme / user defined colors. At present I'm using Clear Looks with custom colors and "random" elements in the system ignore my color settings/preferences.

Clearlooks doesn't have any support for gtk3.

Verify that by looking in /usr/share/themes/Clearlooks. There's no gtk-3.0 folder. The default Lubuntu theme has it.

---

