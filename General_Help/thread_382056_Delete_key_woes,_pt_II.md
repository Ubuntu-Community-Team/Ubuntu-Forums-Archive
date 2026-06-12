---
title: "Delete key woes, pt II"
date: 2007-03-11
forum: General Help
---

### Post by skwishybug on 2007-03-11
So, I finally got around to checking to see what the status of my delete key is in a shell setting, and it works there.

I tried to be creative and edit my /etc/X11/xorg.conf file and entered the name of the layout that works from the keyboard layout control in Gnome. All that served to do was crash Gnome and give me the opportunity to try out my abilities to return things to the way they were (was able to, thankfully).

So, the question I have is how to get my delete key working?

My xorg.conf says:
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

I need to changed this so that my HP Pavillion dv1000 laptop delete key works.

Note, when I go into the keyboard layout control and change to the HP Pavillion zt11xx layout all the keys work the way they are expected to.

Any suggestions?

---

### Post by skwishybug on 2007-03-12
Got it figured out. Apparently had nothing to do with the keyboard layout -- somewhere/somehow I managed to map the delete key to a completely different command (pausing music :-?).

---

