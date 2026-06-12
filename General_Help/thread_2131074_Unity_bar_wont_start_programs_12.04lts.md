---
title: "Unity bar wont start programs? 12.04lts"
date: 2013-03-31
forum: General Help
---

### Post by Sxynerd on 2013-03-31
I have a newer install of 12.04LTS on my laptop and for some reason a couple of the programs wont actually start when clicked.  They'll pulsate but not actually start.  I've had them installed previously without issue.

The ones that work:
Dash
Chrome
Firefox
Software center
system settings
Guake
imagewriter


The ones that Don't.
GIMP
Blender

---

### Post by deadflowr on 2013-03-31
Try running them in a terminal.
Simply type gimp, and see what the output is.
Post the results here.

---

### Post by Sxynerd on 2013-03-31
"gimp: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory"

Thanks


" blenderX Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  32
  Current serial number in output stream:  32
Segmentation fault (core dumped)"

---

### Post by efflandt on 2013-03-31
It looks like you have some issue with graphics (GL). What video card/chip do you have and are you using default video drivers, or others (and how did you install them)?

---

