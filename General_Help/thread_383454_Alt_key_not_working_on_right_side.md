---
title: "Alt key not working on right side"
date: 2007-03-13
forum: General Help
---

### Post by RyanGT on 2007-03-13
I am trying to get Edgy setup and running and things are going fairly well.  I am having one annoying problem though: my alt key doesn't work on the right side of my keyboard (it works fine in windows, so it is not the keyboard).  For example, at a bash prompt, typing ctrl-v and then alt-y produces
ryan@am2:~$ ^[y
when using the left alt, but
ryan@am2:~$ y
when using the right all.

How do I fix this?

If it matters, I have a Microsoft Natural Multi-media keyboard.

Thanks,

Ryan

---

### Post by buuntuu! on 2007-03-13
looks as if you have selected the wrong keyboard-layout.
under ubuntu go: >system>preferences>keyboard
there you can select the appropriate layout

---

### Post by mbeierl on 2007-03-13
Check for this section in your /etc/X11/xorg.conf:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
#        Option          "XkbOptions"    "lv3:ralt_switch" <-- if you have this, comment it out
EndSection

```

Restart X.  That might do the trick!

---

### Post by RyanGT on 2007-03-13
Commenting out the line mentioned above seems to have done the trick.  I couldn't find a keyboard layout that solved the problem.

Thanks for the simple and effective solution.

Ryan

---

