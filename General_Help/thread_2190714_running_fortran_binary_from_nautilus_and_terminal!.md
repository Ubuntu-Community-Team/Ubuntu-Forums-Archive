---
title: "running fortran binary from nautilus and terminal?!?"
date: 2013-11-28
forum: General Help
---

### Post by Termo on 2013-11-28
I have a scientific fortran program compiled with gfortran that gives different output (only for some of the internal calculations) depending if I run the binary from terminal (./program), or I double click it in nautilus?!? It works from a double click but fails from terminal...

WHY? 

What is the difference between executing from nautilus and from terminal?

---

### Post by Termo on 2013-11-28
Well found the difference for the behaviour in the code... the sum function gives a wrong (very small) number when running from terminal but not from nautilus. Now I changed to a do loop to calculate the sum (like in old style fortran) and it works fully...

Still puzzled about the difference between the two ways of executing a file.

---

