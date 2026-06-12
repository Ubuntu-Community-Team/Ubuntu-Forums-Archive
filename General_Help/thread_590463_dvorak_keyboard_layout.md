---
title: "dvorak keyboard layout"
date: 2007-10-24
forum: General Help
---

### Post by thinsoldier on 2007-10-24
Where do I find the option for a Dvorak keyboard layout and how do I set it up so I can quickly switch back and forth between Dvorak and regular US English QWERTY?

---

### Post by Aathos on 2007-10-24
Go to System->Preferences->Keyboard.  On the "Layouts" tab click the Add button, and choose US English as the layout and Dvorak as the variant, then click Add.  On the "Layout Options" tab, click on "Group Shift/Lock Behavior" and choose what key combination you want to use to change the layout.  There may be something else that changing the group does, but as far as I can tell, it just changes the keyboard layout.

Hope that helps.

---

### Post by thinsoldier on 2007-10-24
thanks


....dammit I'm really starting to hate Ubuntu. I'd say even windows is more consistent in many areas.

Applications > Other > keyboard
Applications > Other > keyboard layout
  AND!
System > Preferences > keyboard

ARE ALL COMPLETELY DIFFERENT THINGS.

Also that keyboard menu seems to not be able to decide between the terms "Super" and "Win-key"

---

### Post by der_joachim on 2007-10-25
I have 2 different ways to switch on the fly. My wife uses good ol' qwerty, but I prefer dvorak. The keyboard section oy my xorg.conf looks like this:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
	Option         "XkbOptions" "grp:alt_shift_toggle,compose:ralt,eurosign:5,altwin:super_win"
EndSection

```
This way, using Alt+Shift works just like in Windows: you switch layouts.

When I'm logged in, I occasionally switch back to qwerty. Alt-Shift is not an option, since some programs use Alt-Shift-<key> combinations. For that, I have a keyboard layout applet in my KDE taskbar. I,m pretty sure Gnome has one as well. One left click will do the trick.

IIRC, the windows keys and super keys are the same. The MS flag apparently reminds people of Superman's cape. ;)

Good luck.

---

