---
title: "C Library Files"
date: 2007-10-21
forum: General Help
---

### Post by kingdogbert on 2007-10-21
I've got a fresh install of Ubuntu, and I'm trying to build a VLSI tool called 3DMagic. However, when compiling this tool, However, I'm missing key library files I would have expected to have. I'm missing general C files like:
stdlib.h
stdio.h
string.h

Others I'm not so familiar with:
ctype.h
sys/types.h
sys/time.h

It just goes on and on like that. I assume there's some general C library package. Can anyone tell me where to get it? Thanks

---

### Post by raul_ on 2007-10-21
sudo aptitude install build-essential

---

