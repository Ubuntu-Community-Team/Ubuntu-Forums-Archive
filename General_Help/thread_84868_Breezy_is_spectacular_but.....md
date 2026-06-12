---
title: "Breezy is spectacular but...."
date: 2005-11-01
forum: General Help
---

### Post by jmrush on 2005-11-01
I have 2 problems from the start,one of them is "invalid" encoding when viewing folder names in XP partitión.It seems not to recognize accents or special keys.The other one is keyboard detecting.There's no way to change it to spanish keys unless you do it from the terminal (xsetkeyboard -layout "es") everytime you start session.Is there a way to fix both?

Thanks for the rest.

---

### Post by cbkm on 2005-11-01
I presume this can be done in /etc/X11/xorg.conf

Mine shows:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

```

Presumably you can just set XkbLayout option to "es", and then restart X (Ctrl+Alt+Bksp).

---

### Post by trash-can on 2005-11-01
Ofcourse one can define keyboard layout in /etc/X11/xorg.conf, but there is also applet for GNOME panel called Keyboard Indicator. The good thing about defining layouts in xorg.conf is that it is independent of desktop(Gnome/KDE) you use.

This is what I have in mine xorg.conf:```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "lv,ru"
        Option          "XkbOptions" "grp:shift_toggle,grp_led:scroll"
        Option          "XkbVariant" "apostrophe,phonetic,"

EndSection

```"XkbOptions" "grp:shift_toggle,grp_led:scroll" line means that I can switch layouts by pressing both Shift keys & that Scroll Lock led will indicate the switch to second layout.

---

### Post by rwabel on 2005-11-05
you have to add utf8 in your fstab for mounting fat32 partitions. for example:
/dev/hda1       /media/hda1     vfat    defaults,user,rw,exec,umask=000,utf8

I hope it works now

---

