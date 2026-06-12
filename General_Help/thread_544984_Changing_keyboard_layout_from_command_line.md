---
title: "Changing keyboard layout from command line"
date: 2007-09-07
forum: General Help
---

### Post by urIkon on 2007-09-07
Dearest Smart-computing Aficionados,

I use the standard Dvorak keyboard layout, but every so often a family member or friend needs to borrow my box, and I have to switch my layout back to a standard QWERTY.  I was wondering if anyone knows a simple way to do this from the command line, so that I could script it up for time-savingness and make it possible for my more technically challenged guests to switch back and forth, as remembering the whole system-preferences-keyboard method seems too daunting a task for the majority of them. 

Thanks in advance!:popcorn:

---

### Post by mbsullivan on 2008-01-22
You can use the "setxkbmap" from the command line for this.  Although I don't know what layout you are using, in the case of switching from US English (QWERTY) to US English (Dvorak), the following commands should work:

(1) QWERTY -> Dvorak
```
setxbkmap dvorak
```

(2) Dvorak -> Qwerty
```
setxbkmap us
```

Although this introduces the difficulty that it is hard to use the command line if you can't type in a given keyboard layout, you could create links to scripts to execute this command, or hotkey it if you want.

Hope this helps!
Mike

---

### Post by belecubration on 2008-03-07
There is a typo... the command is setxkbmap and not setxbkmap

---

### Post by unutbu on 2008-03-07
The following will allow the user to switch between dvorak and qwerty by pressing both Shift keys at the same time:

Just to be safe:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg-backup.conf

```

Then edit /etc/X11/xorg.conf. Search for "CoreKeyboard" and then change the surrounding text to something like this:

```

Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver "kbd"
    Option "CoreKeyboard"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc105"   # Your XkbModel may be different. Keep yours.
    Option "XkbLayout" "dvorak,us"                         # These are the 
    Option "XkbOptions" "grp:shift_toggle,grp_led:scroll"  # important lines
EndSection

```

Note that in gnome-terminal, the Ctrl-C and Ctrl-Z keys will not be remapped properly.
That is, if dvorak is your default, then after switching to qwerty, the qwerty user will have to press Ctrl-I in order to produce a Ctrl-C, and Ctrl-/ in order to produce a Ctrl-Z.

The setxbkmap solution has the same deficiency.
I'd really appreciate it if someone knows how to fix this.

Reboot, and if you like it, you can 
```

sudo rm /etc/X11/xorg-backup.conf 

```

Also note that you may receive a warning message the first time you log in: Gnome will say it was expecting your old xorg.conf keyboard configuration and ask if really want to use the new one now. When you say yes, any additional tweaks you made to your layout using System>Preferences>Layout Options will have been wiped out. (Swapping of Ctrl and Caps_Lock, for example). You may also find that your Alt key is no longer acting like a Meta. 

The solution is simple: Go to System>Preferences>Layout and click the radio button to select dvorak as the default keyboard. Then for some reason your Alt key will work again.

Hope this helps.

---

