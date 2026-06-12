---
title: "building old software - can't find X includes"
date: 2020-08-07
forum: General Help
---

### Post by AnotherBrian on 2020-08-07
i'm getting a message when trying to configure an old software program (this is pre compile). 
it says "can't find x include". 

what package do i need?  thx

---

### Post by TheFu on 2020-08-07
It is looking for header files.  X is short for X11 usually. I'd start with these packages:
```
libxt-dev/focal 1:1.1.5-1 amd64
  X11 toolkit intrinsics library (development headers)
libx11-dev/focal 2:1.6.9-2ubuntu1 amd64
  X11 client-side library (development headers)
```

When you look at the Makefile, what are the exact libraries used?  I'd expect to see something like **-lx11 -lxt** somewhere in there.
-lx11 --> libx11.so.  Every library has 1 or more objects - .o files inside.  Each .o file has 1 or more .h or .hpp or .H files which contains the calling specification for each function or method if C++.

I made a huge leap because you said exactly "X includes" - if "X" was a generic placeholder, nobody can help.  The 'x includes' is worrisome. 'x' isn't the same as 'X', at least in my experience.

---

