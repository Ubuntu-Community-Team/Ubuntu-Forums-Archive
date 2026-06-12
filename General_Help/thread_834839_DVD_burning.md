---
title: "DVD burning"
date: 2008-06-19
forum: General Help
---

### Post by JJRrocket on 2008-06-19
Hey guys, i recently installed Ubuntu off the live CD.

For some reason, whenever I try burn to a blank CD/DVD the burning program does not accept the disc ( i have tried Nero Linux and Brasero).  It doesn't even seem to even spin the damn thing it just keeps saying 'no disc'.  If i put in a dvd/cd with something on it, I can access it just fine so it seems software related.  Funnily enough, when I was using the live CD, and had yet to install linux, the burning program, Brasero, would work perfectly.

Any ideas?
thanks

---

### Post by VMC on 2008-06-19
From a Terminal what is the ouput of this:

```
wodim -checkdrive
```

---

