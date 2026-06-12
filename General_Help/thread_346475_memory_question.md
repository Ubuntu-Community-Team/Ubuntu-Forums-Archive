---
title: "memory question"
date: 2007-01-25
forum: General Help
---

### Post by oldmanstan on 2007-01-25
i upgrade my ram from .5gb to 2.5gb, all new boards, they test fine.  i just want to clarify how linux handles the memory.  when i first booted the machine top showed about 2.1 gb free.  now after running programs and closing them and whatnot for awhile i have only about 300mb free and i dont have anything open that should be taking up very much.  i've run and closed google earth a couple times and some other memory hogs but they are now all closed.

anyway, my question is whether linux just keeps the data in memory for possible use later or if it should be clearing it out when i close a program which might indicate something broken on my sys?

thanks

---

### Post by kidders on 2007-01-25
Hi there,

> **oldmanstan said:**
> my question is whether linux just keeps the data in memory for possible use later or if it should be clearing it out when i close a program which might indicate something broken on my sys?

The answer depends on how you know how much free memory you have. Different methods may well give you different answers. It may be the case that 2.1G is allocated (but not necessarily in use). The Linux kernel does not tend to deallocate memory (especially virtual memory) when it's finished with it (which would be a waste of CPU cycles).

I doubt you should be concerned.

---

### Post by yabbadabbadont on 2007-01-25
The numbers are slightly misleading.  Any unused memory is generally used as disk cache.  This cached memory is freed for program usage by the kernel as needed.

```
/home/bubba $ free -m
             total       used       free     shared    buffers     cached
Mem:           756        313        443          0         29        183
-/+ buffers/cache:        100        656
Swap:          964          0        964
```
As you can see, 29M of the used memory is buffers, and 183M is cache.

Edit: Too slow.  :)

---

### Post by kidders on 2007-01-25
> **yabbadabbadont said:**
> Edit: Too slow.  :)Nope! Perfectly good point... and I didn't mention it. :-) Thanks!

---

### Post by oldmanstan on 2007-01-25
thank you both greatly, that's what i needed to know

i was figuring that something like that was the case but wanted to check

thanks!

---

