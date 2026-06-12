---
title: "[SOLVED] hibernation don't work - not enough swap"
date: 2008-03-21
forum: General Help
---

### Post by TheLions on 2008-03-21
since I have 2GB RAM and only 1GB of swap i can't put Ubuntu on hibernate cause swap is to small
[B]
SO my question is how to make it to go hibernate without resizing swap???[/B]

---

### Post by dcstar on 2008-03-21
> **TheLions said:**
> since I have 2GB RAM and only 1GB of swap i can't put Ubuntu on hibernate cause swap is to small
[B]
SO my question is how to make it to go hibernate without resizing swap???[/B]

Take out 1GB of ram or put "mem=1024M" in your boot string.

---

### Post by fsmithred on 2008-03-22
Make a swapfile. No re-partitioning necessary.

[http://www.linux.com/feature/113956](http://www.linux.com/feature/113956)

---

### Post by TheLions on 2008-03-22
> **dcstar said:**
> Take out 1GB of ram or put "mem=1024M" in your boot string.

:lolflag:

---

