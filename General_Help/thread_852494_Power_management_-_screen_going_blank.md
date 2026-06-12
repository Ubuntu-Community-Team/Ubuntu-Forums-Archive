---
title: "Power management - screen going blank"
date: 2008-07-07
forum: General Help
---

### Post by AeroSpace on 2008-07-07
My screen goes blank every so often when not moving the mouse or typing. It comes back when the mouse is moved, so I'm assuming that it is the effect of some power management setting saying something like "turn the screen off after 10 mins of idle".

How can I access and change this setting, from the console? I don't have and don't really want to install gnome-power-manager or anything like that. (I have a minimal install, no GNOME or anything).

Many thanks

EDIT: I have installed XFce (not Xubuntu), but I don't think thats doing it because I can't find anything in the XFce settings.

---

### Post by lucaspr on 2008-07-08
> **AeroSpace said:**
> My screen goes blank every so often when not moving the mouse or typing. It comes back when the mouse is moved, so I'm assuming that it is the effect of some power management setting saying something like "turn the screen off after 10 mins of idle".

How can I access and change this setting, from the console? I don't have and don't really want to install gnome-power-manager or anything like that. (I have a minimal install, no GNOME or anything).

Many thanks

EDIT: I have installed XFce (not Xubuntu), but I don't think thats doing it because I can't find anything in the XFce settings.

I've got exactly the same question. Where can I turn off the 'screen saver' for a console only installation?

---

### Post by lucaspr on 2008-07-13
Little sunday-kick...

Nobody has the answer to this question?? Or is it to easy to answer?:wink:

---

### Post by lucaspr on 2008-07-13
Maybe I've found it on my own... :wink:
If this line solves my 'problem' it is pretty easy!
```

sudo setterm -blank 0

```

Entered my password and now the waiting starts! I will edit this entry to tell the answer for future users who also didn't know about the command setterm...

```

man setterm

```


It did.. That little line (the first one of course :)) solved my problem. Screen won't blank anymore! So Aerospace hope it solves yours too!

---

