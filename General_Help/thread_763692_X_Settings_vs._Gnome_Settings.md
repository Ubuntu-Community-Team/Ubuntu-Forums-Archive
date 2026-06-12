---
title: "X Settings vs. Gnome Settings"
date: 2008-04-23
forum: General Help
---

### Post by emale07 on 2008-04-23
When I boot I get this message:

> The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc105", layout "us" and no options.

Which set would you like to use?

I've been choosing X Settings, and have not had any trouble that I'm aware of.  Any idea what's going on and what I can do to remove the issue?

---

### Post by markharding557 on 2008-05-05
what happens if you choose gnome
it could be that the incorrect keyboard was chosen in set up have a look in xorg.conf to see whats in the section input device line,if it says pc101 change it to pc105
here is mine so you can see
> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

---

