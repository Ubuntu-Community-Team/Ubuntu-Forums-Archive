---
title: "Avant window navigator keeps exiting"
date: 2007-02-17
forum: General Help
---

### Post by billdotson on 2007-02-17
Avant window navigator just keeps shutting down.  I don't know why I have all the dependencies and beryl installed.

---

### Post by reacocard on 2007-02-17
Could you please run avant-window-navigator from the terminal and give us the output?

---

### Post by billdotson on 2007-02-18
sgtmattbaker@sgtmattbaker:~$ avant-window-navigator

(avant-window-navigator:18121): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

(avant-window-navigator:18121): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

---

### Post by reacocard on 2007-02-18
What version of AWN are you using? Did you install from source or the repo?

---

### Post by billdotson on 2007-02-18
I just downloaded the source from [http://code.google.com/p/avant-window-navigator/]("http://code.google.com/p/avant-window-navigator/")
I am pretty sure.

---

### Post by reacocard on 2007-02-19
> **billdotson said:**
> I just downloaded the source from [http://code.google.com/p/avant-window-navigator/]("http://code.google.com/p/avant-window-navigator/")
I am pretty sure.

The last stable version from the site also requires a patched libwnck. I'd recommend just installing AWN from my repo instead, as it has everything necessary. See here for instructions: [http://ubuntuforums.org/showpost.php?p=2120903&postcount=68](http://ubuntuforums.org/showpost.php?p=2120903&postcount=68)

---

