---
title: "Screen overlaps?"
date: 2007-07-18
forum: General Help
---

### Post by SnakeByte29 on 2007-07-18
I have a strange problem with my desktop in that the screen seems to (for lack of a better word) overlap itself. About a half-centimeter of the screen that should be on the right has moved to the left. Has anyone else experienced this and know how to fix it?

This is what it looks like:
[[IMG]http://img362.imageshack.us/img362/2967/imga0341vu5.th.jpg[/IMG]](http://img362.imageshack.us/my.php?image=imga0341vu5.jpg)

I apologize for the quality of the picture but the screenshot program does not show anything wrong.

---

### Post by longlegs on 2007-07-21
Hi ,
The screen shot makes me think that you have a crt type monitor, not an lcd. The pic you show is the result of having the horiz/vert sync/refresh too hi or otherwise incorrect for your monitor. 
If possible, use system>preferences>screen resolution to set the resolution down to say 800x600 that almost any monitor will handle.
If this corrects the problem, go up in steps to see where the problem recurs.
If you do not have other resolutons available in system>preferences>screen resolution then you will have to edit /etc/X11/xorg.conf and add resolutions.
For more on how to do that do a search for 1440x900 or for uncle spellbinder

good luck
longlegs

---

