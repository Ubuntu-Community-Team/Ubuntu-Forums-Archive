---
title: "French Logitech Elite Keyboard (Y BF38) shift key"
date: 2007-11-02
forum: General Help
---

### Post by chiquita on 2007-11-02
Hi,

I have been searching for days after I installed kubuntu but am still stuck :my shift keys do not work whatever I tried to fix it and I think it is due to the X mapping. I think I did not install any package affecting X.

I cannot type the percent sign, or mu, or pound, interrogation mark... even with the caps lock on (but capital letters are accessible this way).

Here is the keyboard settings in xorg.conf :
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "latin9"
EndSection

I do not know much about the inet file but still, I tried to modify it without success.
When using xev, my shift keys do not raise any event.
lineak does not fix anything either.
I could use kvkbd but it is really unproductive...

If someone could help me, it would be really appreciated :)

---

### Post by FredB on 2007-11-02
Try answering this on ubuntu-fr.org forums. You'll have more answer than here.

---

