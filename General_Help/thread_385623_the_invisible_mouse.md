---
title: "the invisible mouse"
date: 2007-03-15
forum: General Help
---

### Post by mastermonil on 2007-03-15
okay i just booted from livecd (btw im a noob at linux) and got into ubuntu.
but my mouse pointer just doesnt show..like i can move my mouse and guess but i kinda want my pointer. lz help

---

### Post by heimo on 2007-03-15
> **mastermonil said:**
> okay i just booted from livecd (btw im a noob at linux) and got into ubuntu.
but my mouse pointer just doesnt show..like i can move my mouse and guess but i kinda want my pointer. lz help

This sounds funnier than it must be... I suppose you already tried to change the pointer by going to System->Preferences->Mouse->Pointers?

Next thing I'd try is to edit /etc/X11/xorg.conf and add a line to the mouse section 'Section "InputDevice"':
```
Option SWCursor

```Or it might be:
```
Option SWCursor "True"

```

---

