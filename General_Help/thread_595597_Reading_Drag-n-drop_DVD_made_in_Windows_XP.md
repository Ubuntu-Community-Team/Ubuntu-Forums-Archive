---
title: "Reading Drag-n-drop DVD made in Windows XP"
date: 2007-10-28
forum: General Help
---

### Post by roboknight on 2007-10-28
I seem to have an issue reading a DVD created via the Windows Drag-n-Drop method.  I have a DVD that I have stored several sessions (well, at least 3 anyway) to using the Windows XP drag-n-drop.  When I try to read this in my Sony drive (the drive that actually created the disc in the first place), it comes up with an error from the logs (dmesg):

UDF-fs: No partition found (1)

which leads to it not mounting the volume.  Presumably this is because the drag-n-drop format from Windows XP isn't supported by my system for one reason or another.  Is this support available?  What project do I need to add it?  Everyone says google is your friend, but only when you already know where to look, which in this case, I apparently don't.

Thanks for any help,
roboknight.

---

### Post by daengbo on 2007-10-29
What program were you using to drag and drop? This page:
[http://forums.techguy.org/windows-nt-2000-xp/535574-dvd-drag-drop.html](http://forums.techguy.org/windows-nt-2000-xp/535574-dvd-drag-drop.html)
and several others I found state that XP doesn't have this ability. Did you install any DVD-writing software?

---

### Post by roboknight on 2007-10-29
I know it does with CDs (and something makes me think DVDs also, because I've used it somewhere else without 3rd party software, but not in this case, as you'll note)... but after hex-editing a dump of the DVD I took , it appears it was created with Ulead's UDF software (I don't remember the name, I don't use XP anymore.  Hence the problem.).

---

