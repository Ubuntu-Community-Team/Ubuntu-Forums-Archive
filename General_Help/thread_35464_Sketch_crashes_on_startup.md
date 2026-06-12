---
title: "Sketch crashes on startup"
date: 2005-05-19
forum: General Help
---

### Post by dare2dreamer on 2005-05-19
Any ideas? I'm completely stumped.

Sketch 0.6.15

~> sketch
Traceback (most recent call last):
  File "/usr/bin/sketch", line 34, in ?
    Sketch.main.main()
  File "/usr/lib/sketch-0.6.15/Sketch/Base/main.py", line 148, in main
    run_script = options.run_script)
  File "/usr/lib/sketch-0.6.15/Sketch/UI/skapp.py", line 184, in __init__
    geometry = geometry)
  File "/usr/lib/sketch-0.6.15/Sketch/UI/skapp.py", line 103, in __init__
    self.init_tk(screen_name, geometry)
  File "/usr/lib/sketch-0.6.15/Sketch/UI/skapp.py", line 213, in init_tk
    geometry = geometry)
  File "/usr/lib/sketch-0.6.15/Sketch/UI/skapp.py", line 108, in init_tk
    className = self.tk_class_name)
  File "/usr/lib/python2.4/lib-tk/Tkinter.py", line 1569, in __init__
    self.tk = _tkinter.create(screenName, baseName, className, interactive, wantobjects, useTk, sync, use)
TypeError: function takes at most 4 arguments (8 given)

---

### Post by Zelut on 2005-05-19
For something specific like this I'd suggest checking out the support by sketch.  I did a search & it looks like its now called skencil (?) [http://www.nongnu.org/skencil/](http://www.nongnu.org/skencil/)

It looks like there is a newer version 0.6.16 that you could try (sometimes version updates do the trick) or post your crash on their forum / mailing list.  Unfortunately I'm not familiar with sketch/skencil so I dont have more tips for you.

---

### Post by dare2dreamer on 2005-05-19
I'm trying to get sketch working because it is used as a back-end by inkscape to save into several file types. They appear to be working, but I'm not 100% sure. I was going to fire up this version of sketch to compare file outputs, so an upgrade to a new app may not be a viable solution.

---

