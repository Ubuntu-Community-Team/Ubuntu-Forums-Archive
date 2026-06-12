---
title: "4 GB RAM is only used as 2.7 GB"
date: 2007-04-19
forum: General Help
---

### Post by slick123 on 2007-04-19
Hello all,

i recently upgraded my RAM to 4 GB (known perfectly by my BIOS) 
After a fresh install of Ubuntu 7.04 using Kernel 2.6.20-15-generic 
ubuntu has available only 2.7 GB RAM (shown in gnome system-manager)
what did i miss in installation or how do i let ubuntu know that it should use 4GB ?

---

### Post by not_a_commie on 2007-04-19
Check in your BIOS for a setting to (re-) map memory replaced by devices beyond the 4GB mark. I know most Tyan boards have that option.

---

### Post by not_a_commie on 2007-04-19
I should add that if you're using a 32bit version, the most any one process can recognize is 3GB. You'll need a 64bit OS to use more than that in a single program.

---

### Post by slick123 on 2007-04-19
Thanks commie  for the reply

The bios option is not set. This was what i checked first anyway. 
You have the point with the 32 bit os  i think.. I will have a look at 64 bit kernel then but i was a bit surprised because i thought that generic should support up to 4 GB since it's in address Space 2^32=4294967296 
i wrongly assumed then that linux whould do the things better than windows xp :-)

regards

slick

---

