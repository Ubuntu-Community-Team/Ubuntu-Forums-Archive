---
title: "Unable to rmdir"
date: 2005-07-10
forum: General Help
---

### Post by Gary Powers on 2005-07-10
Ripped a CD using Goobox and it created a "locked" directory owned by root, which has a subdirectory in it and several tunes in the subdirectory.  I am unable to get rid of that directory because I do not have the necessary permissions. 

I have attempted to change ownership, change permissions, I have used rmdir --ignore-fail-on-non-empty [directory].

First real difficulty in 8 months on Ubuntu (I'm running Hoary).  Not a bad track record.  

Would appreciate any thoughts.

Gary

---

### Post by Leif on 2005-07-10
Doesn't sudo rm -R dir work ?

---

### Post by Gary Powers on 2005-07-10
[QUOTE=Leif]Doesn't sudo rm -R dir work ?[/QUOTE]

It didn't work last evening, but worked perfectly this morning.  Maybe I used the wrong syntax yesterday.

Anyway, thanks much Leif.

Gary

---

