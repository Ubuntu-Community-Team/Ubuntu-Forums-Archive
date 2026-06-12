---
title: "Resize handles don't appear in Open Office"
date: 2007-10-28
forum: General Help
---

### Post by the_it on 2007-10-28
I  just reported a dark themes incompatibility issue in the openoffice bugtracker.  I have another issue, but i don't know whether it's ubuntu generated or openoffice generated.  I'll be downloading a vanilla Openoffice later to check.

When I draw a vector object in openoffice, I'm used to selecting it then dragging the reize (or rotate) handles to resize it.  In ubuntu gutsy, the resize handles don't appear, and I have to resize manually.

I don't think this is normal behavior.  Anyone know any fixes?

---

### Post by the_it on 2007-10-28
By resize manually, I mean I have to right click, go to the properties, then resize by number.  It's not good enough for me.

For now I have to look for another application to do my vector drawings.

---

### Post by hikaricore on 2007-10-28
I'm not sure why you would do vector drawing in Open Office in the first place.  O.o

You'd be better off with Xara or possibly Krita which are both in the Gutsy repos.

---

### Post by the_it on 2007-10-29
I removed openoffice.org-gnome and openoffice.org-gtk and it solved the problem.

So it's a bug in gtk integration.  In which case I've already done my part to report it to the OpenOffice crew.

I'll check out xara and krita, but oodraw is convenient.  What's wrong with it?

===

I hope this xara isn't in multiverse because it's nonfree or something.  I can't depend on something like that.

===

just checked the site.  Passes by my book.  Wonder why it's not in universe? I've never heard of it before.

---

### Post by the_it on 2007-10-29
Xara seems more shapre oriented than object oriented, which is the behavior i'm looking for in this particular vector drawing app.  From my initial usage, it seems like nothing more than a faster version of inkscape.

Prebuilt shapes and connection data are important for a certain class of vector diagrams.  I'll try to make something in it, but I don't think I'll find it useful for my particular case.

---

