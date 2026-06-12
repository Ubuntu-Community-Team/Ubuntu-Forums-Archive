---
title: "how do you change the default menu icon in Ubuntu Gnome?"
date: 2008-04-22
forum: General Help
---

### Post by jesusfreak107 on 2008-04-22
I use Ubuntu Gutsy, with Gnome (duh!).  Instead of the three-section menu, I have the one Icon that, when clicked, has the dropdown menu.  how do I change this icon?:guitar:

---

### Post by tedt on 2008-04-22
I think you need to replace the file "distributor-logo"

---

### Post by newb1e on 2008-04-22
> **jesusfreak107 said:**
> I use Ubuntu Gutsy, with Gnome (duh!).  Instead of the three-section menu, I have the one Icon that, when clicked, has the dropdown menu.  how do I change this icon?:guitar:

the three-section menu is "Menu Bar" and the one icon is "Main Menu". You can see it in the "add to panel" setting.

---

### Post by jesusfreak107 on 2008-04-22
...and where would that be?

---

### Post by tedt on 2008-04-22
> **jesusfreak107 said:**
> ...and where would that be?

oh there are a bunch . . . 

from the command line run:

locate distributor-logo



the one you want to change depends on the icon theme you have loaded 

you can either write over the file or you can add the file distributor-logo.png to whatever custom icon theme you are running

---

