---
title: "Having trouble getting Gnome Games onto Xubuntu"
date: 2007-10-11
forum: General Help
---

### Post by cmc3887 on 2007-10-11
I recently tried to install Ubuntu onto an older system that I am reformatting to give my grandmother simply to play solitaire and browse the internet. However, the computer wasn't able to run it very well so I was recommended to try Xubuntu instead, which runs great with one exception: it doesn't come with the solitaire games that are really the main reason she wants the computer.

I've tried getting the Gnome Games package from synaptic, but after downloading 31 of the 34 files, it asks me to insert Ubuntu 7.04 i386 CD, which I already have in the drive. So I'm kind of at a stand still.

Alternately, I've tried downloading them from:
[http://live.gnome.org/GnomeGames/Download](http://live.gnome.org/GnomeGames/Download)

But Xubuntu doesn't seem to recognize any of the file types that I'm getting.

---

### Post by por100pre1 on 2007-10-12
```
gksudo software-properties-gtk
```

Uncheck the CD, that should make it stop asking for the disk.

---

### Post by cmc3887 on 2007-10-12
thanks, I'll give this a try when I get home from work.

---

