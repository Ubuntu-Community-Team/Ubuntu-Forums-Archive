---
title: "Ghostscript - no graphics window appears"
date: 2008-03-13
forum: General Help
---

### Post by EricDB on 2008-03-13
I want to work through this textbook on using PostScript to create mathematical diagrams:

[http://www.math.ubc.ca/~cass/graphics/manual/](http://www.math.ubc.ca/~cass/graphics/manual/)

I've run into a problem right away, though.  According to the book, GhostScript ("gs" at the command prompt) should pop up a graphics window, so you can enter commands and see their output immediately.

I have gs installed, and the command-line interface looks exactly like it does in the book, but there is no graphics window.  I can type commands, but I never see their results.

What am I missing?

---

### Post by geraldm on 2008-03-13
Older ghostscript versions assumed the user wanted a graphics window, and provided it.
Newer ghostscript assumes less.  If you want a graphics window, you specify it.
set GS_FONTPATH environment variable to your location of fonts: /usr/share/fonts/gsfonts 
Then
```

gs -sDEVICE=x11 filename.ps

```
Use your filename in place of filename.ps

Gerald

---

