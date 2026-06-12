---
title: "Option &quot;XkbLayout&quot;  is being ignored"
date: 2007-10-05
forum: General Help
---

### Post by Josi on 2007-10-05
I have created a custom Keymap for my Keyboard.
I saved it as 
/etc/X11/xkb/symbols/us_ext

Now I can load it with 
```
 $ setxkbmap us_ext
```
No problem.  But I can't seem to be able to load it from xorg.conf:


```
Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option      "CoreKeyboard"
    Option      "XkbRules"  "xorg"
    Option      "XkbModel"  "pc105"
    Option      "XkbLayout" "us_ext"
EndSection
```


What am I missing?

---

