---
title: "Acer keyboard mistake (I need help to my xorg.conf)"
date: 2006-10-09
forum: General Help
---

### Post by Dumpen on 2006-10-09
Hey.

I'm running on Ubuntu 6.06, and since I am from Denmark I need some special characters, but my xorg.conf doesn't seem to be working at the moment.

The special characters I need is the å, æ and ø

Plus I need to get the shift + 2, to result in the strudel (@)

You can find my xorg.conf here

pastebin.co.uk/3899

Just let me know, if you need anything other information.

Since it wont let me post an url you need to c/p it in to your browser.

But here is the part about my keyboard

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "dk"
Option "XkbVariant" "dk"
Option "XkbOptions" "dk"
EndSection

Greetings Dumpen.

---

### Post by Dumpen on 2006-10-10
Gaah come on, help me :?

---

