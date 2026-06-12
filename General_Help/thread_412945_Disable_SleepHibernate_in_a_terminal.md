---
title: "Disable Sleep/Hibernate in a terminal?"
date: 2007-04-18
forum: General Help
---

### Post by NPALeech on 2007-04-18
I'm trying to compile a rather large program, but every 15 or so minutes my computer goes into sleep mode. I wish to prevent this. Is there anyway you can do this in a terminal? There is no X Server on the box I'm doing the compiling.

Thanks in advance.

---

### Post by snoleo on 2007-08-20
try:

setterm -powersave off
setterm -blank

---

