---
title: "too many errors when comiling"
date: 2007-06-23
forum: General Help
---

### Post by jasonlfunk on 2007-06-23
I have some C code that I didn't write that I am compling and I get errors when I use gcc. Too many to scroll up and read them. How can I direct the output to a file to read it. I have tired the obvious ```
gcc whatever.c > log
``` and it didn't work.

---

### Post by jasonlfunk on 2007-06-23
I figured it out. gcc outputs to stderr which is redirected by >&

---

