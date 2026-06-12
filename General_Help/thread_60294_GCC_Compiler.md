---
title: "GCC Compiler"
date: 2005-08-27
forum: General Help
---

### Post by Halz0r on 2005-08-27
Im trying to install kismet wireless tools, but im having trouble compiling the ./configure file. 

It checks for GCC, CC, C, and IC, then errors that there is no acceptable C compiler in $PATH.

Any hints?

Cheers,
-Halz0r

---

### Post by heimo on 2005-08-27
You could start by installing package build-essential
 ```
sudo apt-get install build-essential
```

---

### Post by Halz0r on 2005-08-27
Ok, further issues with installing kismet. It was unable to find initscr in -lcurses, errors unable to find libcurses.

Any ideas?

---

### Post by spin2cool on 2005-08-28
go into synaptic and do a search for "libcurses"  You may find what you need there.

If it's not showing up, add the repositories listed at [www.ubuntuguide.org](www.ubuntuguide.org)

---

