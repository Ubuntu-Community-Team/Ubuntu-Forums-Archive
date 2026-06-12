---
title: "Graphics cards works fine, but Compiz effects, when enabled, don't."
date: 2008-06-10
forum: General Help
---

### Post by lorgonjortle on 2008-06-10
I have just recently gotten my graphics card driver to work. So now desktop effects can be enabled. (Thanks, Forlong) When I go into the CompizConfig and enable something, it doesn't work. I have tried multiple things. I would like the cube and what not. Why isn't this working?

---

### Post by lavinog on 2008-06-10
in a terminal:
```
compiz --replace
```
post the output here
most likely your card might not be whitelisted

what graphics card do you have?
what does glxgears do?

---

### Post by lorgonjortle on 2008-06-10
I have an ATI Radeon 1100 Xpress.

compiz --replace:
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5975 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```
glxgears:
Worked fine! Looks pretty cool though! (It's three gears running)
```

4818 frames in 5.0 seconds = 963.532 FPS

```

---

### Post by lavinog on 2008-06-10
I am not sure if i understand the problem.
It looks like compiz is working...what is it that tells you that it doesn't work?
if you leave the terminal open after typing compiz --replace does it work?

what happens when you press ctrl-alt-rightarrow or super (windows start key) and E?

---

### Post by lorgonjortle on 2008-06-10
Ok, everything is working now. Thanks to the wonderful Ubuntu community. I needed to enable desktop effects for compiz to start working. I now have the cube and ring and everything. So, on my want list there is one last thing. An animated desktop (Matrix) the falling matrix code. Anyone know how I can get it?

---

### Post by nickdbliss on 2008-06-11
OK mark this thread as solved.thanks :)

---

