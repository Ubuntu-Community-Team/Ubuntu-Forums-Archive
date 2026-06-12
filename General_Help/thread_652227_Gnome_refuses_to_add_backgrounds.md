---
title: "Gnome refuses to add backgrounds"
date: 2007-12-28
forum: General Help
---

### Post by Ryoushi19 on 2007-12-28
For some reason, when I try to add new desktop backgrounds on gnome, it just refuses to do it.  It does absolutely nothing.  Anyone have any ideas on this?

---

### Post by rune0077 on 2007-12-28
How exactly do you add the background? Through Appearances? 

You could try finding the background on the net, then, instead of downloading it, right-click it and choose "use as background" (this is assuming that you use Firefox).

---

### Post by kshane on 2007-12-28
> **Ryoushi19 said:**
> For some reason, when I try to add new desktop backgrounds on gnome, it just refuses to do it.  It does absolutely nothing.  Anyone have any ideas on this?

In what way are you trying to add backgrounds?

Kevin

---

### Post by Ryoushi19 on 2007-12-28
By using the appearance menu.  Using "Set as wallpaper" in firefox or eye of gnome works, for some reason, but then, for another reason, it won't let me manage the backgrounds properties, and it doesn't go into my backgrounds list in "appearance", either.

---

### Post by kshane on 2007-12-28
> **Ryoushi19 said:**
> By using the appearance menu.  Using "Set as wallpaper" in firefox or eye of gnome works, for some reason, but then, for another reason, it won't let me manage the backgrounds properties, and it doesn't go into my backgrounds list in "appearance", either.

Suggestion:  Put all of your background images in a single directory in your home directory, then just right click on your desktop and choose Change Desktop Background and use this as your program to select.  Once you set the images in the directory you made, they'll all show and you can change the background in a couple of clicks.

Kevin

---

### Post by rune0077 on 2007-12-28
If you're using Compiz, and the cube, there's also a way to select background images under that plugin. Could it maybe be a conflict between the two? If the cube is enabled, try to be sure no background image is set there (though there shouldn't be, unless you've done it yourself).

If not, then what happens when you select "Add" under Appearances? Just nothing, or do you get to still pick a file and then nothing happen, or do you get some kind of message?

---

### Post by Ryoushi19 on 2007-12-28
I still get to try and pick a file it just does nothing to that file.  I tried looking at the XML backgrounds config, and when I do add a file, nothing is added to the list.  I can, however, manually add in files, via typing in XML codes, but that's a pain.  The GUI is there to make that XML for you, so why isn't it?

---

### Post by FuturePilot on 2007-12-28
Could you try running it from the terminal and try adding a wallpaper? It might give some type of error.
```
gnome-appearance-properties
```

---

### Post by Ryoushi19 on 2008-01-01
No error is returned upon attempting to add a new background, however, upon startup, it returns the following:

(gnome-appearance-properties:7089): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;

(gnome-appearance-properties:7089): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;

(gnome-appearance-properties:7089): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;

(gnome-appearance-properties:7089): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;

(gnome-appearance-properties:7089): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;

(gnome-appearance-properties:7090): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed

---

