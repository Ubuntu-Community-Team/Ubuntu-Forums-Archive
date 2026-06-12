---
title: "Some system apps don't run in Gusty"
date: 2007-10-21
forum: General Help
---

### Post by Yes on 2007-10-21
When I try to edit my menu bar, open "Default Printer", "Hardware Information", "Main Menu", "Language Support", "Printing" (I have two "Printing", one works, the other doesn't), "Restricted Drivers Manager", "Update Manger", "Software Sources", and "Screens and Graphics", I get the following error:

```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
```

Again, this is in Gusty.  My install went fine, it seems like it's a programming error in the programs?

Thanks.

---

### Post by nrune on 2007-10-21
Yep same issue here.  Not sure what is going on. see my thread

[http://ubuntuforums.org/showthread.php?t=584364](http://ubuntuforums.org/showthread.php?t=584364)

No solution as of yet.

---

### Post by Yes on 2007-10-21
Well, at least I'm not alone =/.  I think your gnome-terminal problem might be a different bug, because I don't get that when I launch a terminal.  Although that could just be because I use Gnome.

---

### Post by Yes on 2007-10-23
Bump.

---

### Post by Yes on 2007-10-23
Since no one seems to be able to fix this, is it possible for me to use other versions of these programs?  I assume some people have them working in Gusty, would I just be able to download their's?  Or would I run into problems?

---

### Post by fragos on 2007-10-23
I have no such problems starting with a clean install from the live CD.

---

### Post by Yes on 2007-10-23
Yeah, this problem seems to be pretty isolated.  I would really like to avoid having to reinstall Gusty, if at all possible.

---

