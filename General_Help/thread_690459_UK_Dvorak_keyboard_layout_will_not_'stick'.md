---
title: "UK Dvorak keyboard layout will not 'stick'"
date: 2008-02-07
forum: General Help
---

### Post by phenest on 2008-02-07
I've been used to using the Dvorak keyboard layout for some time, but have come across a problem.

(I am running Hardy alpha 4 but I don't think it's relevant.)

When I login to X, it uses Qwerty even though the layout is set to Dvorak in Preferences>Keyboard-Layout. To 'fix' the problem, I simply set it up again, or, click the keyboard model and click OK. If I logout, it reverts back to Qwerty even though it's set to Dvorak in /etc/default/console-setup

Any other places to check?

---

### Post by phenest on 2008-02-09
Spot the typo:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkVariant"    "dvorak"
EndSection

```

Why didn't I see that before!

---

