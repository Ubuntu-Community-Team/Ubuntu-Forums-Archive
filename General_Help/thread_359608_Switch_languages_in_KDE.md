---
title: "Switch languages in KDE"
date: 2007-02-12
forum: General Help
---

### Post by MasterOfMuppets on 2007-02-12
I'm on Kubuntu Edgy and I have the following problem:
I have US-English and Hebrew defined as keyboard layouts, but I can't switch between them both via keyboard. I can click on the icon and switch it, but I write in both languages a lot so this is not an option. I can use ALT+CTRL+K to switch from English to Hebrew, but not the other way around. When I turn on sticky switching, it simply resets itself to OFF when I close the System Settings window. I've edited xorg.conf a zillion times, tried a whole lot of things, but nothing seems to work :(.
This is my xorg.conf:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,he"
        Option          "XkbOptions"    "grp:alt_shift_toggle"
EndSection

```

I've seen many many threads about this, but none seem to solve this problem. Please help...

---

### Post by MasterOfMuppets on 2007-02-12
I think I found out what the problem is. xkb might be reseting itself because I don't have xxkb installed. Probablt got removed when I went into pure KDE... I would greatly appriciate it if someone would affirm my theory. Anyways, I can't install xxkb for some peculiar reason.
Here's a link to the xxkb problem:
[http://ubuntuforums.org/showthread.php?t=359673]("http://ubuntuforums.org/showthread.php?t=359673")

---

