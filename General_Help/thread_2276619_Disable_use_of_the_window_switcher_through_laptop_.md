---
title: "Disable use of the window switcher through laptop touchpad?"
date: 2015-05-03
forum: General Help
---

### Post by Giwayume on 2015-05-03
There is a weird shortcut in Ubutntu that I keep accidentally hitting on my laptop touchpad, and I'm not sure how to disable it.

Basically if I'm holding two fingers down on the touchpad (like when you're scrolling) then I tap a third finger the window switcher pops up and switches to the most recently opened window.

Is there a way to remove this shortcut, like in compiz config or something?

---

### Post by Giwayume on 2015-05-07
Is this place dead?

---

### Post by tgalati4 on 2015-05-07
What desktop environment are you running?

In Mouse Preferences, Touchpad tab, try unchecking "Enable mouse clicks with touchpad".

I'm running MATE and I don't have that issue, so perhaps it is normal behavior in Unity?

---

### Post by Giwayume on 2015-05-08
Yes, I'm using Unity.

Disabling all of the settings in the "Mouse & Touchpad" menu does not disable this functionality, only if I decide to disable the touchpad altogether does it stop (obviously).

I'm sure there's a setting for this in compiz somewhere, I just can't find it.

The dialog I'm trying to get rid of looks like this:

[http://i.imgur.com/T4sbFMN.png](http://i.imgur.com/T4sbFMN.png)

---

### Post by mc4man on 2015-05-08
I don't believe this is fixable thru some setting as seems to be a bug.
(- here can dupe by 2 finger on touchpad with a double tap using 3rd.

---

### Post by Giwayume on 2015-05-09
I ended up following the answer here and recompiled Unity without its built-in multi-touch gestures, since I don't use them anyways.

[http://askubuntu.com/questions/57586/how-can-i-disable-arbitrary-default-multitouch-gestures-in-unity](http://askubuntu.com/questions/57586/how-can-i-disable-arbitrary-default-multitouch-gestures-in-unity)

---

