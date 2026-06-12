---
title: "Changing icons seems so random"
date: 2014-02-22
forum: General Help
---

### Post by samwillc on 2014-02-22
Hi everyone,

I have installed sublime text 2 to /opt and am trying to change the icon to match the eNumix-uTouch icon pack. The following reveals the locations of various icons:

```

find / -type f -iname "sublime_text.*"

```

which outputs (amongst other results):

```

/usr/share/icons/hicolor/16x16/apps/sublime_text.png
/usr/share/icons/hicolor/128x128/apps/sublime_text.png
/usr/share/icons/hicolor/48x48/apps/sublime_text.png
/usr/share/icons/hicolor/32x32/apps/sublime_text.png
/usr/share/icons/hicolor/256x256/apps/sublime_text.png
/usr/share/icons/eNumix-uTouch/apps/48/sublime_text.svg //I PUT THIS ONE IN MANUALLY AND LINKED TO IT FROM SUBLIME_TEXT.DESKTOP
/opt/sublime_text_2/Icon/16x16/sublime_text.png
/opt/sublime_text_2/Icon/128x128/sublime_text.png
/opt/sublime_text_2/Icon/48x48/sublime_text.png
/opt/sublime_text_2/Icon/32x32/sublime_text.png
/opt/sublime_text_2/Icon/256x256/sublime_text.png

```

I don't use hicolor theme, and sometimes I find icons in '/usr/share/icons/hicolor/scalable/apps' which affect my icons (even though I'm not even using this theme). And '/usr/share/pixmaps', what about this one? Is there no standard that applications must use to implement an icon?

For sublime text 2, the .desktop file has an entry 'Icon=sublime_text'. So which icon is actually being used (a) in plank (using elementaryos) and (b) in applications menu?

Is there an order of precedence when the OS looks for an icon? It all seems so random, different apps seem to put icons in different places. Any input would be most appreciated, thanks :)

Sam.

---

### Post by Toz on 2014-02-22
> **samwillc said:**
> 
Is there an order of precedence when the OS looks for an icon? It all seems so random, different apps seem to put icons in different places. Any input would be most appreciated, thanks :)

Sam.
It follows the freedesktop [Icon Theme specification]("http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html"). The important information to help you decode which icon is used is located in the icon theme's .theme file (in the root of the icon theme's directory structure).

---

### Post by samwillc on 2014-02-22
Great, thanks :)

---

