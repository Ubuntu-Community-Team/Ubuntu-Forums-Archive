---
title: "Desktop Icon Labels"
date: 2008-06-15
forum: General Help
---

### Post by detroit/zero on 2008-06-15
Can anybody tell me how to get rid of the black background around the desktop icon labels? I thought I saw it in a how-to somewhere along the line, but can't for the life of me find it now.

I made a screenshot to show what I'm talking about if you don't understand or if I'm unclear:
[CENTER][IMG]http://img119.imageshack.us/img119/7235/screenshotet0.png[/IMG]
[LEFT]
I'd just like the text to appear without a background, or be able to set it to transparent.. however you want to word it.

Thanks for the help.
[/LEFT]
[/CENTER]

---

### Post by bapoumba on 2008-06-15
> **detroit/zero said:**
> Can anybody tell me how to get rid of the black background around the desktop icon labels? I thought I saw it in a how-to somewhere along the line, but can't for the life of me find it now.

I made a screenshot to show what I'm talking about if you don't understand or if I'm unclear:

I'd just like the text to appear without a background, or be able to set it to transparent.. however you want to word it.

Thanks for the help.

Are you using gnome or Xfce ?

---

### Post by detroit/zero on 2008-06-15
Sorry... Gnome.

---

### Post by bapoumba on 2008-06-15
> **detroit/zero said:**
> Sorry... Gnome.

Okay, I'll have to look then.
There is a conf file you can edit in Xfce that does it quite nicely. Are you sure the tutorial was for GNOME ?

---

### Post by detroit/zero on 2008-06-15
Yes.. I used it back in either my Edgy or Feisty days, I just don't remember how it went. I don't think it was through the Configuration Editor. If I remember right, it was a quick edit in a conf file somewhere like you say..

I could be wrong, but I haven't found anything in conf editor..

---

### Post by bapoumba on 2008-06-15
Okay, I have not used GNOME in some time now. Looking around I found the gnome-color-chooser package (in universe):
[LP page]("https://launchpad.net/gnome-color-chooser")
[sourcegorge page]("http://gnomecc.sourceforge.net/")

Not what you were looking for, but I did not (with a quick look) find a conf file to edit..

Edit: was it with the .gtkrc-2.0 (it may have a different number now) conf file? I found things for the font color, but not the background.

---

### Post by detroit/zero on 2008-06-15
That did the trick! Thanks a million!

---

