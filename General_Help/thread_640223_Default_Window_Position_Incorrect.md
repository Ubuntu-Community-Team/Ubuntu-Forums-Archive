---
title: "Default Window Position Incorrect"
date: 2007-12-13
forum: General Help
---

### Post by technel on 2007-12-13
Hi,

Whenever I open a program up, the default window position is right up against the top edge of the screen. Therefore I can't see the title bar. I do have a panel at the top, but even if I move it, the window's default position then becomes outside of the monitor. It is always just the titlebar that is concealed. I have a keyboard shortcut to move windows, and that allows me to see them, but it is REALLY annoying.

Any ideas? I have attached a screenshot for illustrative purposes. Thanks!

(Note: Yes, I am using Compiz Fusion. ATI graphics card, FGLRX)

---

### Post by dpar on 2007-12-14
[http://ubuntuforums.org/showthread.php?t=639545](http://ubuntuforums.org/showthread.php?t=639545)

---

### Post by Schalken on 2007-12-14
you need to enable the compiz plugin "place windows", which is responsible for appropriately placing new windows on the screen, otherwise they just default to having the content area begin at (0,0) (top left of the screen).

---

### Post by dpar on 2007-12-14
Or, just use one panel on the bottom.:)

---

### Post by technel on 2007-12-14
> **dpar said:**
> Or, just use one panel on the bottom.:)

Unfortunately, I tried that. "I do have a panel at the top, but even if I move it, the window's default position then becomes outside of the monitor." Heh.

> **Schalken said:**
> you need to enable the compiz plugin "place windows", which is responsible for appropriately placing new windows on the screen, otherwise they just default to having the content area begin at (0,0) (top left of the screen).

That fixed it, thanks a lot! I had seen that when I was troubleshooting this and thought that enabling it would be a bad idea (I thought it was only for using keyboard shortcuts to place windows).

---

### Post by mathenge on 2008-04-08
Thanks for the "Place Windows" tip. That also solved my problem and things are working and being placed very nicely.

---

