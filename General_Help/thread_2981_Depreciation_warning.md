---
title: "Depreciation warning?????"
date: 2004-11-02
forum: General Help
---

### Post by brschmid on 2004-11-02
what does this mean?> /usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)

---

### Post by ynef on 2004-11-02
Deprecation errors mean that something in the code is getting old and has been replaced in newer versions of the language in question. In your specific case it means that you should not use "mainloop" but "main" instead. I haven't got a clue about anything even remotely related to Python, but that's what the error message says anyway.

---

### Post by brschmid on 2004-11-02
[QUOTE=ynef]Deprecation errors mean that something in the code is getting old and has been replaced in newer versions of the language in question. In your specific case it means that you should not use "mainloop" but "main" instead. I haven't got a clue about anything even remotely related to Python, but that's what the error message says anyway.[/QUOTE]
 hmmm, well anyone know how to fix it?

---

### Post by jdusablon on 2004-11-02
Maybe tell us what you are trying to do that generates that error.

I've often found that when something fails that way, the problem is solved by just doing it another way!

---

### Post by brschmid on 2004-11-02
[QUOTE=jdusablon]Maybe tell us what you are trying to do that generates that error.

I've often found that when something fails that way, the problem is solved by just doing it another way![/QUOTE]
 trying to run gdeskcal

i d/l'd it via the SPM and i can run it from the "run app" gui but when i try to run it from the terminal i get that warning.

---

### Post by jdong on 2004-11-02
It means the program was written for an earlier version of Python. Since then, the language undergone some changes (i.e. new names for old tricks), and they're phasing out some functions the program's trying to call. Maybe notify the author of the issue, but make sure you give him your python version number.

P.s. it's deprecation (i.e. to deprecate -- to express desire for removal of), not depreciation (i.e. your house after a new landfill's built in front of it)

---

### Post by jdusablon on 2004-11-02
Hey, if I remember correctly,  brschmid and I both had the same problem running gdesklets. Same idea, would run from Run App... but not from terminal. I assume that some python apps/scripts are designed to be run from within gnome (or maybe from within X?)

How does one tell how to run something with Run App... or terminal?

---

### Post by Rancoras on 2004-11-02
It really doesn't matter which way you run it.  It's just a warning.  It doesn't cause the program not to run.  The warning is just hidden when you run it from the run applet.

---

### Post by brschmid on 2004-11-04
[QUOTE=Rancoras]It really doesn't matter which way you run it.  It's just a warning.  It doesn't cause the program not to run.  The warning is just hidden when you run it from the run applet.[/QUOTE]
 yea it runs correctly from the terminal and i have it set to start automatically upon startup.

---

