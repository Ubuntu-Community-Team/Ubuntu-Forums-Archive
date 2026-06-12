---
title: "From Transparent to Solid theme."
date: 2020-05-04
forum: General Help
---

### Post by alvinrr on 2020-05-04
Can someone please help me with making the Nordic darker theme to be more solid and not transparent. I really liked the theme but I don't like its transparency.

here are the codes
[https://paste.ubuntu.com/p/CtQtSYpWXp/](https://paste.ubuntu.com/p/CtQtSYpWXp/)

---

### Post by Dennis N on 2020-05-04
> **alvinrr said:**
> Can someone please help me with making the Nordic darker theme to be more solid and not transparent. I really liked the theme but I don't like its transparency.

Transparency is set in the rgba color code. Look for rgba(a,b,c,t) throughout the file you displayed. 't' is the transparency value in the range 0 &#8804; t &#8804; 1.
0 = completely transparent, 1 = no transparency (opaque).
 
for example rgba(24, 37, 185, 0.8) is 80% opaque shade of blue.

---

### Post by alvinrr on 2020-05-05
> **Dennis N said:**
> Transparency is set in the rgba color code. Look for rgba(a,b,c,t) throughout the file you displayed. 't' is the transparency value in the range 0 &#8804; t &#8804; 1.
0 = completely transparent, 1 = no transparency (opaque).
 
for example rgba(24, 37, 185, 0.8) is 80% opaque shade of blue.

Thank you very much Dennis N. You've been helping me a lot in this forum.

---

