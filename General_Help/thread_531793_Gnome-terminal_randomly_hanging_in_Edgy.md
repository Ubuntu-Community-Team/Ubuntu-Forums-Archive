---
title: "Gnome-terminal randomly hanging in Edgy"
date: 2007-08-22
forum: General Help
---

### Post by MST3Kakalina on 2007-08-22
I recently did a fresh upgrade from Dapper to Edgy.  Everything has gone well for the past few days, but now suddenly gnome-terminal hangs. 

I don't think it was going to Edgy that did it.  Rather, I suspect it either has something to do with the latest updates or my attempt to get gnutella to work (which is another thread in and of itself).  I've read [this]("http://ubuntuforums.org/showthread.php?t=285512") thread and made the suggested change to my xorg.conf file:

```
Section "Extensions"
	Option "Composite" "false"
EndSection
```

with no luck.  I also removed a few files I had to install in my attempt to upgrade gnutella.

When I try to run gnome-terminal in konsole (I'm in Kubuntu), I get this:

```
Gdk-CRITICAL **: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed

```

It doesn't hang all the time, though.  It seems to me that before I connect to the internet, gnome-terminal behaves normally.  A simple workaround would be to open a window before I connect and keep it open while I surf the web, true, but I would still like to fix this problem (because don't we all occasionally close windows we mean to keep open?).

The threads I've seen for this problem are all from last year, so I assume by now someone has figured it out for real?  Checking the known bug/workarounds thread has yielded nothing, though it's late and my eye might have missed it.

Any help is much appreciated!

---

