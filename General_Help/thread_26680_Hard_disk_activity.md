---
title: "Hard disk activity"
date: 2005-04-13
forum: General Help
---

### Post by xilun on 2005-04-13
Hi,

I encounter regular hard disk activity from an unknown origin, every 2 sec.
I tried to use strace on every running processes and grep "write", but without any success (writes of userland processes I can strace are only to pipes...). Anyway I discovered that the HD activity takes place at the same frequency and phase as some userland processes writes to pipes. There is even more activity when i'm logged in...

The fact that those disk access as a soft cause is confirmed by the number of cache buffer which changes at the same rythm in free output.

Does anybody knows where it comes from ? My HD makes quite noise, and such regularity is very tedious...

Thanks,
Guillaume Knispel

---

### Post by Whiffle on 2005-04-13
How much system RAM do you have?  If the computer is low on ram it will be hitting the swap all the time.

---

### Post by xilun on 2005-04-13
256 Mo

xiltmp@box:~$ free
             total       used       free     shared    buffers     cached
Mem:        256808     250252       6556          0     150200      24192
-/+ buffers/cache:      75860     180948
Swap:      1052248          0    1052248


I should have no trashing problem.

---

