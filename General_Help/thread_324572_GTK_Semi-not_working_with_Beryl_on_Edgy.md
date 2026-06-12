---
title: "GTK Semi-not working with Beryl on Edgy"
date: 2006-12-23
forum: General Help
---

### Post by digital_me on 2006-12-23
So... I use Beryl 1.3, gnome, XGL, and Edgy.  Beryl runs like a dream, but GTK themes don't fully work.  by this I mean that I see the correct buttons for the themes (sometimes), I see the theme applied to the panel, and some of the colors are applied.  I made sure I had the gtk2-engines-pixbuf package installed, like someone suggested elsewhere, and gnome-settings-daemon was started, and I restarted it to no avail.  Restarting X also accomplishes nothing.  I'm at a loss here, so any help would be appreciated.

Thanks!

---

### Post by Azakus on 2006-12-24
Post an example screenshot. That will help diagnose the problem.

---

### Post by ~LoKe on 2006-12-24
If it's a Murrine theme, then make sure you have the latest murrine engine (0.31).

---

### Post by digital_me on 2006-12-24
I've also noticed that gtk has the same problems even when I'm not running beryl.
[The image is too large to just put in the thread.]("http://digitalme.name/gtk.png")

Note, this theme should make pretty much everything dark, which obviously, it's not.

---

### Post by Azakus on 2006-12-24
I don't belive those parts on the panel actually change with the theme, ever. Try making the background color of the panels invisible and see if that looks better.

---

### Post by _simon_ on 2006-12-24
Just tried that theme and it does make everything black for me.
This is what it should look like: [http://www.gnome-look.org/content/show.php?content=45829](http://www.gnome-look.org/content/show.php?content=45829)

Doesn't help much but confirms that the theme works as you are expecting it to.

Just had a thought... do you have a custom .gtkrc-2.0? as that will override the theme.

In your /home, show hidden files and look for that. if it's there, then rename it and log out then back in.

---

### Post by digital_me on 2006-12-24
@_simon_: Thanks, that did the trick!  Looks like KDE made a .gtkrc-2.0 that was messing it up... :\

---

### Post by Azakus on 2006-12-24
That is a nice looking theme!

---

### Post by _simon_ on 2006-12-24
> **digital_me said:**
> @_simon_: Thanks, that did the trick!  Looks like KDE made a .gtkrc-2.0 that was messing it up... :\

Good good! :D

---

