---
title: "several apps don't change keyboard layout"
date: 2019-07-17
forum: General Help
---

### Post by pianoist on 2019-07-17
I'm stacked with a problem of changing keyboard layout, currently, in 2 apps: skype and Reaper.
Currently, i'm using fctix to switch between English, Russian and Pinyin, so far the problem existed only in Reaper, I just thought it doesn't  got fctix and never mind.
My current system is Xubuntu 19.04 and on the laptop is installed Xubuntu 18.04 LTS also with the same fctix conf, where skype was installed and worked almost fine (Reaper - not).
Now, installed skype on the PC (19.04) I found the same switching problem, and edited xorg.conf:
```
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option       "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us,ru"
    Option        "XkbVariant"    ",winkeys"
    Option        "XkbOptions"    "grp:ctrl_shift_toggle,grp_led:scroll"
EndSection
```
But it doesn't work.

Also, laptop 18.04 (where problem is for Reaper but not for skype) I installed with core language of Russian. But 19.04 on the PC was installed just with English.

For other apps(terminal, FF, mousepad, sublime) in both systems works as xorg switching, as fctix hotkeys. What can it be and how to fix?

Thanks for help!

[Edited] Nope, xorg switching on ctrl+shift doesn't work at all. Only fctix. But switching edited in the preferences (keyboard -> layout) worked, but not for theese two apps

---

