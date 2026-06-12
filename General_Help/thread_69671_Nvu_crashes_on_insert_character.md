---
title: "Nvu crashes on insert character"
date: 2005-09-27
forum: General Help
---

### Post by petr on 2005-09-27
Running from a shell I get
 /usr/lib/nvu-1.OPR/run-mozilla.sh: line 159: 8102 Segmentation fault "$pg" $(1+"$@"}

 ...

 OK the problem seems to be that firefox has to set up some files.  To do that, one needs to run firefox as root with the (undocumented) -H option

>sudo firefox -H

After that Nvu can insert characters.

Things you learn..

Petr.

---

### Post by muka on 2005-09-28
When I have problems like that, I simply completely remove the program with Synaptic, and then re-install it via Synaptic.

---

