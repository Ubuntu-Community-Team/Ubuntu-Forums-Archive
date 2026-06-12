---
title: "Icon sizing Nautulus"
date: 2007-07-09
forum: General Help
---

### Post by stchman on 2007-07-09
Hello all, I know that in Nautilus-->Preferences you can selct icon size at 25, 50, 75, 100 via the drop down menu.  What I wanting to know is fi there is an in between way to manipulate these numbers as they also select desktop icon size.

Thanks

---

### Post by stalker145 on 2007-07-10
> **stchman said:**
> Hello all, I know that in Nautilus-->Preferences you can selct icon size at 25, 50, 75, 100 via the drop down menu.  What I wanting to know is fi there is an in between way to manipulate these numbers as they also select desktop icon size.

Thanks

If I am misunderstanding your question, please let me know.

I think what you are asking is how to change the desktop icon size?

If so, open up gconf-editor (<alt><F2> gconf-editor), navigate through apps~>nautilus~>icon_size (I think) and change the field that says (probably) 'normal'. I have mine set to 'small' and it works for my taste. I believe smallest works as well (or it's smaller), but that's ubsurdly tiny.

I'm sorry for being vague in most spots. I'm on my work Win2K machine and am working from memory.

If this isn't what you were asking, please let me know and I'll try helping.

---

### Post by Jim Danner on 2007-08-07
I have been looking for this as well. With the Preferences in Nautilus, and with the Configuration editor (in the key /apps/nautilus/icon_view/default_zoom_level), you have a choice of default icon sizes:
smallest = 25%
smaller = 50%
small = 75%
standard = 100%
large = 150%
larger = 200%
largest = 400%

This choice is still a bit limited. On my screen and for my taste, around 60-65% would be ideal. Is it possible, for example, to define an additional standard size? Let's say "smallish" at 65%?

They tell me everything in Linux is configurable, so it must be possible... (it sure is in Windows;)).

Any expert who knows this?

---

### Post by stchman on 2007-08-07
> **Jim Danner said:**
> I have been looking for this as well. With the Preferences in Nautilus, and with the Configuration editor (in the key /apps/nautilus/icon_view/default_zoom_level), you have a choice of default icon sizes:
smallest = 25%
smaller = 50%
small = 75%
standard = 100%
large = 150%
larger = 200%
largest = 400%

This choice is still a bit limited. On my screen and for my taste, around 60-65% would be ideal. Is it possible, for example, to define an additional standard size? Let's say "smallish" at 65%?

They tell me everything in Linux is configurable, so it must be possible... (it sure is in Windows;)).

Any expert who knows this?

Exactly, I want to know.

---

### Post by Jim Danner on 2007-08-08
It doesn't look like the Nautilus programmers are about to add zoom customization (as of August 2007). In one [bug report]("http://bugzilla.gnome.org/show_bug.cgi?id=327709"), a developer said half a year ago: "I don't think it's that usefull and it can produce not optimal results." As of the most recent Nautilus version (2.19.6, released July 31), it certainly hasn't been added.

I don't understand the reasoning here - Nautilus already allows zooming ("stretching")  to any arbitrary size, albeit on the level of individual icons, and by the way those icons look fine to me.

Has Microsoft's "We know what's good for you" virus hit the Nautilus developers? Hopefully not! It's a wonderful file browser (I'd prefer it over Windows Explorer any day), but it does seem to lack customization options.

Maybe someone has written a "Nautilus extension" to add the functionality. Haven't found one yet.

---

