---
title: "change colour of text on panels?"
date: 2007-02-08
forum: General Help
---

### Post by syxbit on 2007-02-08
i changed my panels to transparent, but now if i have a desktop bg that's dark, I can't read the date/time, or "Applications/Places/System"
can you change the colours so they show up?

---

### Post by ~LoKe on 2007-02-08
```
gedit ~/.gtkrc-2.0
```
Paste this:
> style "panel"
{
    fg[NORMAL]               = "#FFFFFF"
}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

---

### Post by syxbit on 2007-02-08
nice.
works like a charm!

how on earth did you figure that out!

---

### Post by ~LoKe on 2007-02-08
Research!

---

### Post by Lord Darth Vader on 2007-02-12
Wow! Thank you!

---

### Post by Sceiron on 2008-03-30
I'm trying to do this myself, but i ran into following:

I dont have a .gtkrc-2.0 but a .gtkrc-1.2-gnome2
is this a older type of customization file ? how do i proceed?

when i try to gedit this file, the context of the file is only this:
> # Autowritten by gnome-settings-daemon. Do not edit

include "/home/sceiron/.gtkrc.mine"

any ideas ?

---

### Post by Oldsoldier2003 on 2008-03-30
> **Sceiron said:**
> I'm trying to do this myself, but i ran into following:

I dont have a .gtkrc-2.0 but a .gtkrc-1.2-gnome2
is this a older type of customization file ? how do i proceed?

when i try to gedit this file, the context of the file is only this:


any ideas ?

create the file and it will work.

---

### Post by Sceiron on 2008-03-30
Thank you, it works like a dream. Stupid me :P
But on the other hand, does this mean that the DM not is loading 2 files instead of one?
So it uses more time (teoretically) to get it up and running ?

---

### Post by Oldsoldier2003 on 2008-03-30
> **Sceiron said:**
> Thank you, it works like a dream. Stupid me :P
But on the other hand, does this mean that the DM not is loading 2 files instead of one?
So it uses more time (teoretically) to get it up and running ?
I tried it and didn't notice any difference in load time. theoretically it would add a fraction of a second in load time or so you would think. But either way i decided that having the text in white was more distracting than anything else. I've grown quite used to the cleaner look with the text bleeding into the background :)

---

### Post by mcduck on 2008-03-30
> **Sceiron said:**
> Thank you, it works like a dream. Stupid me :P
But on the other hand, does this mean that the DM not is loading 2 files instead of one?
So it uses more time (teoretically) to get it up and running ?

 Of course _in_theory_ it takes more time to load 2 files instead of one, but the time it takes to load such a small text file is so small you'd really have hard time finding a way to even measure it.. We are not talking about seconds, or even tenths of seconds, but of a lot smaller times.

Besides, the system still has to check if the .gtkrc-2.0 file exists, no matter if you have it or not, so reading the file as well really makes no difference.

---

