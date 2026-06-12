---
title: "How to stop OOO making thumbnails?"
date: 2007-12-07
forum: General Help
---

### Post by rune0077 on 2007-12-07
Okay, here's my problem: I deleted my .thumbsnail folder (on purpose), but now, when I save a file in OOO-writer, Nautilus displays it as a thumbnail?!? That's stupid, since 20 files that are just pages with text on them look pretty identical as thumbnails. So, my question, does anyone know how to stop OOO files from being saved as thumbnails and instead just being displayed with their mimetype icon?

---

### Post by rune0077 on 2007-12-07
bump

---

### Post by geirha on 2007-12-07
I don't get thumbnails of open office documents, neither on edgy nor gutsy. However, it's most likely gnome/nautilus that spawns these thumbnails (not ooo). Run "gconf-editor" and browse to /desktop/gnome/thumbnailers. If there is an entry for open office documents there, you should be able to disable it.

---

### Post by rune0077 on 2007-12-07
There's no OpenOffice documents in thumbnailers editor. I tried unchecking all text-like filetypes (basically all the ones associated with Evince), but it changed nothing. 

I found out, that if I go to my newly generated /.thumbnails and delete the OOO documents there, then they revert back to their original mimetype icon. However, this only last until I save the file again, and then they turn back to a thumbnail. That's pretty weird if you ask me. I kinda do suspect OpenOffice of having something to do with this, but I'm not sure at all.

---

