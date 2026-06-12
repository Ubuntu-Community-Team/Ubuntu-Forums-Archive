---
title: "error in gdb prevents debugging"
date: 2007-01-07
forum: General Help
---

### Post by malk on 2007-01-07
Hello recently gdb has become a problem. When i try to read the file for symbols i get this message > /bin/awake.../build/buildd/gdb-6.4/gdb/dwarf2read.c:5491: internal-error: could not find partial DIE in cache

process i used was gdb cd bin file awake . Normally it would read the file symbols and i could then type run but now it gives that error and asks if i want to quit gdb if i type no it continues but does not give error output. Any suggestions on what could be a problem or how to fix this?
Thanks
Malk

---

### Post by malk on 2007-01-10
No ideas? I have tried removing and reinstalling but did not work.
Malk

---

### Post by majoridiot on 2007-01-10
that is a known bug that was fixed.  you should upgrade to the latest gdb and see if that fixes
it.  if not, there was a patch available.  google gdb and "could not find partial DIE in cache"
for more info.

---

### Post by malk on 2007-01-22
Sorry for the delay. I upgraded and as you said it fixed the gdb problem.
Thx
Malk

---

