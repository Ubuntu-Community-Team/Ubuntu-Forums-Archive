---
title: "Keyboard mapping problems in Gutsy"
date: 2007-12-03
forum: General Help
---

### Post by indie_design on 2007-12-03
Hi,

I am having troubles with getting my keyboard mapping working in Gutsy.

Problems:

1. alt is not sent to terminal (which breaks a third party terminal app I use)
2. shift-3 is not "UK pound symbol" just "3" (all other shift-number keys work ok)
3. Windows/Super keys dont seem to work at all.

Things I have tried:

- Playing around with keyboard short cuts and the gnome keyboard preferences.
- Checking the xorg.conf:
<pre>
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "uk"
        Option          "XkbVariant"    "uk"
EndSection
</pre>
- upgrading

Things it could be:

- I use compiz-fusion (from the main repository)
- I actually installed Kubuntu, but then saw the light and installed gnome - I could have missed something here.
- I still have KDE installed, as I revert to this occasionally (see previous)

Anyhow, any help anyone could give would be much appreciated. :)

Cheers!

---

### Post by indie_design on 2007-12-05
Incase anyone else has the same problem, I managed to fix problem 1:

In gconf-editor: apps->metacity->general->mouse_button_modifier can be changed to <Super> or simply Disabled.

Still having problems with keyboard mapping, if anyone can help?

---

