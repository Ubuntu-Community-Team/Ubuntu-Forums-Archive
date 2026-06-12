---
title: "Gnome menu transparency"
date: 2008-04-30
forum: General Help
---

### Post by noiseordinance on 2008-04-30
Anyone know how to make the gnome menu transparent? I've found how to make the entire menu bar transparent through compiz but i just want the actual dropdown menu...

---

### Post by warbread on 2008-04-30
In Compiz Settings Manager, in the 'General Settings' and under the Opacity tab, you can specify specific programs' opactiy settings.  Put in ```
name=gnome-menu
```.

---

### Post by franket on 2008-04-30
I try to do, but it does not transparency. I do follow this.

In Advanced Desktop Effects Settings (Dialog box CompizConfig Settings Manager) -> Opacity settings 


I click add and insert this.

Opacity Windows : name=gnome-menu
Opacity window values : 0

then log out and log in


my main menu does not transparency? or I do not correct. I try to change Opacity window values my main menu is same.

---

### Post by warbread on 2008-04-30
Whoops, my mistake.  What you want is 'popupmenu'.  Not name='', but just 'popupmenu'.  There seems to be a bug in the values, or at least the scale is akward.  A setting of 15490  for the opacity window values works for me.

---

