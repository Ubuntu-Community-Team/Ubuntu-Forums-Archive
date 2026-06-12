---
title: "Problems with Xorg + keboard"
date: 2004-11-19
forum: General Help
---

### Post by paul.hendrick on 2004-11-19
hi there,
since ive upgraded to xorg from hoary, i cant use some keys properly on my keyboard. notably ´ and ¨.(single/double quotes)
i have to press the key twice for it to show up on the screen. its annoying!
if i press the single quote key, then e, i get é. im not sure why, since i think im using the right layout.
any ideas?

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc101"
        Option          "XkbLayout"     "gb"
EndSection


```

---

### Post by ynef on 2004-11-19
Do you really have a keyboard with just 101 keys? Maybe that's the reason...

---

### Post by daniels on 2004-11-19
[QUOTE=paul.hendrick]hi there,
since ive upgraded to xorg from hoary, i cant use some keys properly on my keyboard. notably ´ and ¨.(single/double quotes)
i have to press the key twice for it to show up on the screen. its annoying!
if i press the single quote key, then e, i get é. im not sure why, since i think im using the right layout.
any ideas?[/QUOTE]You almost certainly want pc104, and then put 'Option "XkbOptions" "menu:compose"'.  Your menu key then becomes a Compose key, where you string together multiple characters to form one.  For instance, compose-u-" is ü, compose-o-/ is ø, compose-e-' is é, compose-a-e is æ, compose-!-! is ¡, et al.

---

### Post by Julius on 2004-11-19
Install the package "xlibs" from Hoary (I had a similar problem and that solved it). (Read it at [http://ubuntuforums.org/showthread.php?p=20956#post20956](http://ubuntuforums.org/showthread.php?p=20956#post20956))

---

