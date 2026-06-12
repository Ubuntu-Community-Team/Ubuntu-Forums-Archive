---
title: "Problems with Metacity/Emerald"
date: 2008-06-03
forum: General Help
---

### Post by kylziel on 2008-06-03
I just got into using Compiz-Fusion, and like it a lot.  I want to use the Emerald theme management instead of Metacity, but don't know how to turn off Metacity (as it seems to be Gnome's default) so that only Emerald runs.  Right now, the only thing changes in themes do in Emerald is change the title bar. (And I have to do that by ALT+F2, and then emerald --replace, every time) If I go into the Metacity settings, it still changes things like window layout, taskbar color, etc.

I want, especially, the taskbar to match with the Emerald theme.

Thanks ya'll.

---

### Post by Ocxic on 2008-06-04
try installing the fusion icon. this allows you to switch with a tray icon, and should allow you to set a default.

if not, you could always add "emerald --replace" to your startup items.

---

### Post by magicmanfk on 2008-06-05
> **Ocxic said:**
> try installing the fusion icon. this allows you to switch with a tray icon, and should allow you to set a default.

if not, you could always add "emerald --replace" to your startup items.

What I did was have two start up commands; "emerald --replace" and "gtk-window-decorator --replace", then choose whichever one depending on which theme type I was using and leave the other unchecked. Seems to be working well for me.

---

### Post by mcduck on 2008-06-05
Metacity and Compiz are just window managers, they aren't even supposed to change anything else.

The way your applications look like is defined by your GTK2-theme. Even when this theme is selected in the same window where you can choose the Metacity- and icon themes, it has nothing to do with Metacity.

If you want to make Compiz use Emerald instead of the gtk-window-decorator for window themes you can define it in Compiz settings (install compizconfig-settings-manager, if you haven't already done that).

---

