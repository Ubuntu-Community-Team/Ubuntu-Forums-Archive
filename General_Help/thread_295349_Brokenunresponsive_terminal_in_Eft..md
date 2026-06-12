---
title: "Broken/unresponsive terminal in Eft."
date: 2006-11-07
forum: General Help
---

### Post by Refrozen on 2006-11-07
I've been running this box for quite a while (months), and as such it's no where near an "out of the box" Ubuntu install anymore...

...after the Edgy Eft upgrade (I think?) my X-emulated terminals (but not my Ctrl+Alt+Fx ones) have stopped having any use whatsoever. It starts up, shows username@box:~$ then as soon as I press enter (whether there is a command or not) it just adds a new line to the terminal... no action whatsoever and no further input is "accepted" by the terminal.

I don't even know what more to say about it,a nd I have no idea where to start looking. This happens in gnome-terminal and xterm for sure.

---

### Post by taurus on 2006-11-07
Sounds like the keyboard is all screwed up!  Look in your /etc/X11/xorg.conf for a section about input device for your keyboard...

```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

```

---

### Post by Refrozen on 2006-11-07
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "ctrl:nocaps"
EndSection

---

### Post by Refrozen on 2006-11-26
Frusturated, I did a complete fresh install of Dapper, then upgraded to Edgy again, and have **the same problem**.

For reference, PIII800, 256MB RAM, ATI Rage Fury Pro.

Any advice?

Edit, to elaborte on the first post. I can type in the terminal when I first open it, it's not until I press enter that it stops taking input. It does not run the first command though.

---

### Post by taurus on 2006-11-26
Why not just install Edgy instead of upgrading from Dapper to Edgy!!!

---

