---
title: "Application opens too big in windows mode"
date: 2008-02-18
forum: General Help
---

### Post by RumorsOfWar on 2008-02-18
I have a Blender icon set to open in windowed mode ( blender -w ) but it opens too big, I can't reach the top to minimise it. Blender uses its own hotkeys, so alt/grab can't move it, Other action keys and Compiz effects like 'place windows' don't work either.
  I need that top window bar. Is there a way to set a widowed mode to open at a preset size?

---

### Post by strabes on 2008-02-18
In compiz you can use the "Window Rules" plugin to define the size & location of windows when they appear. Temporarily you could try using Alt+Middle click to resize the window.

---

### Post by RumorsOfWar on 2008-02-18
Thanks, that would probably work, but I've found this info too. ( applicable to any desktop manager...and I happened to find it first.)
[http://www.math.sunysb.edu/~sorin/online-docs/blender/html/a19823.html]("http://www.math.sunysb.edu/~sorin/online-docs/blender/html/a19823.html")
I opened properties in the launcher, and edited the command line to;
```
 blender -p 50 100 1000 700
```
Works well enough in a 1440*900 screen.
This fix only applies to blender, but other apps can be grabbed or resized with alt/ mouse, so this is good.

---

