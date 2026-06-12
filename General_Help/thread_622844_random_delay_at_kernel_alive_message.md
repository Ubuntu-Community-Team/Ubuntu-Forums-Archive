---
title: "random delay at kernel alive message"
date: 2007-11-25
forum: General Help
---

### Post by paradoxni on 2007-11-25
Ok Im using 7.10 64bit and its running well apart from a weird boot delay, which seems to happen randomly, but doesnt stop Ubuntu booting successfully (albeit after waiting for a few mins).

Normally once I turn on the PC and get the POST screens, grub and then I get briefly for about 1 - 2 seconds :
```

Kernel alive
Kernel direct mapping tables xxxxxxxx .....

```
Ubuntu then starts to boot immediately.


However, seemingly randomly, it will pause on the 'Kernel alive' screen and just sit there for at least 2-3 minutes doing nothing, then it will boot Ubuntu as normal. 

It doesnt happen on every boot, but its frustrating having to wait when it does happen (im impatient ;)) Any ideas what I can do to get to the bottom of this?

---

### Post by paradoxni on 2007-11-25
bump :)

---

### Post by zeltak on 2007-11-27
having the same problems from day 1....its really frustrating

i have not find any solution to this even though ive tried some stuff like changing  the boot options (using no splash, trying to define VGA formats etc..) but nothing works...i have yet to see the Ubuntu logo come up since my first install!


zeltak

---

### Post by paradoxni on 2007-11-27
I get the Ubuntu boot logo ok, just takes several minutes to appear SOME times, but most of the time it boots correctly, weird.

---

### Post by mbeierl on 2007-11-27
Is this a laptop?  Could this have anything to do with low CPU power states (ie: does it happen when booting from battery vs. power?)  Just a shot in the dark...

---

### Post by paradoxni on 2007-11-27
sorry no its a desktop

---

### Post by KotZer on 2008-01-08
I have the same error !!! i have 20% chance to boot immediately.. ?Usually i am not so patient and i end up rebooting the system! I havent managed to install ubuntu yet [ because  i have another problem with detecting my software RAID array] 

But this error is serious and a lot of ppl with amd 64 have it, but i dont see anyone proposing a solution. This is crazy ! I have tried every option available on boot and disabled almost everything in BIOS!

 I tried debian testing and i got the same errors 

i have this mobo [http://www.supermicro.com/Aplus/motherboard/Opteron2000/MCP55/H8DM3-2.cfm](http://www.supermicro.com/Aplus/motherboard/Opteron2000/MCP55/H8DM3-2.cfm)
with 2 CPUs and 8gb RAM

What is WRONG ???


> **paradoxni said:**
> Ok Im using 7.10 64bit and its running well apart from a weird boot delay, which seems to happen randomly, but doesnt stop Ubuntu booting successfully (albeit after waiting for a few mins).

Normally once I turn on the PC and get the POST screens, grub and then I get briefly for about 1 - 2 seconds :
```

Kernel alive
Kernel direct mapping tables xxxxxxxx .....

```
Ubuntu then starts to boot immediately.


However, seemingly randomly, it will pause on the 'Kernel alive' screen and just sit there for at least 2-3 minutes doing nothing, then it will boot Ubuntu as normal. 

It doesnt happen on every boot, but its frustrating having to wait when it does happen (im impatient ;)) Any ideas what I can do to get to the bottom of this?

---

