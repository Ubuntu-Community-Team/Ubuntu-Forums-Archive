---
title: "can't create core dump, feisty"
date: 2007-06-03
forum: General Help
---

### Post by Joshua Swink on 2007-06-03
I'm trying to make a bug report, but can't get a core dump. Any hints? Here's how I tried to get one.

```
josh@host:~/test$ ulimit -c unlimited
josh@host:~/test$ dasher
** (dasher:7437): DEBUG: Initialising DasherMain
** (dasher:7437): DEBUG: Initialising DasherEditor

** (dasher:7437): WARNING **: AT_SPI_REGISTRY was not started at session startup.

** (dasher:7437): WARNING **: Could not locate registry
** Message: Could not initilaise SPI - accessibility options disabled

(dasher:7437): Pango-WARNING **: shape engine failure, expect ugly output. the offending font is 'Arial Unicode MS Not-Rotated 10'

(dasher:7437): Pango-WARNING **: pango_font_get_glyph_extents called with null font argument, expect ugly output
Segmentation fault (core dumped)
josh@host:~/test$ ls
josh@host:~/test$

```

---

### Post by fanatik on 2007-06-04
hmm, check in the directory where dasher is located, the core file may be in there...
$ which dasher

---

### Post by fanatik on 2007-06-04
hmm check in the directory where dasher lives, the core file might be in there:
$ which dasher

---

