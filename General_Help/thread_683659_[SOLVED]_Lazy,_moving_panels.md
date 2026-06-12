---
title: "[SOLVED] Lazy, moving panels"
date: 2008-01-31
forum: General Help
---

### Post by camini on 2008-01-31
Hello there.

I've been polishing my ubuntu desktop lately and am running in some annoynaces.

Somehow, the bottom gnome panel seems rock-solid - it is responsive, does not move, hides and unhides- works well.

On the other hand, my second panel, on the right hand-side of the screen does not work too well.
After reboot it is placed at the left of the screen (while I create it at the right side).
Also, it is hidden (which I want), but then to unhide it, I have to carefully hover over the few pixels visible - if I do it rapidly and move up to the screen edge, the panel won't unhide (while my cursor is obviously over it - at the max of the screen).

What's wrong with these panels?  I also found that in the gconf-editor, these right/left panels get a number, whereas bottom/top get a name.. is that normal?

All help appreciated.

cam

---

### Post by camini on 2008-01-31
After extensive reading on gnome panel behaviour it appears that the 'lazy' panel syndrome is a side effect of using the compiz fusion desktop cube effect.  Disabling this effect solves the problem with the 'dead zone' at the very edge of the screen left and right.

So it is solved, let's say.  A bug report for this exists.

One problem I have is that the panel does not want to be placed on the right hand side of the screen and will keep positioning itself on the left side.  Clueless to what that could be though.

If anyone has a clue, let me know.
cam

---

### Post by camini on 2008-03-05
Solved the panel issue as well using gconf-editor and changing value for:

/->Apps->Panel->toplevels->panel_1->y

from -1 to 0

which solved the problem.

---

