---
title: "Running low on memory"
date: 2007-01-10
forum: General Help
---

### Post by jlmorgado on 2007-01-10
Hi there.

I've Ubuntu Server installed on a dual P3 - 500 Mhz with 1Gig of RAM. It's a LAMP based server with SAMBA installed. When I transfer files from one PC in the network to the server or the other way around, the available RAM goes really low, something like 15MB.

I would understand that if some time later, the used RAM would start being released, but it won't. A day later, there is still low free mem.

If I check top, I see that the process that's using the most memory is mysqld with 1.7% (which is a very low amount of RAM for 1Gig installed)...

Could anyone give me some idea about what's going on?

Thanks :)

jlmorgado

---

### Post by az on 2007-01-10
Unused memory is wasted memory.  The stuff cached in ram will stay there until another process actually needs more ram.  It would be a waste of time to clear the ram unless another process needs it.  That way, the next time an application that already is in ram is used, it is more efficient.

---

### Post by jlmorgado on 2007-01-10
:)

Thanks for the fast reply. Ok, I understand that, but keeping almost 800MB in cache, for a whole day, when the machine is really not doing nothing... I know that it is impossible for the kernel to know if the things in cache will be used in the next minute, hour or day, but keeping all that amount of memory occupied for that long...

Is there a way to clean cached files after sometime?

Here's an example of what i'm talking:
server-01:~$ free
             total       used       free     shared    buffers     cached
Mem:       1035632    1018520      17112          0      39976     896600
-/+ buffers/cache:      81944     953688
Swap:       843372        124     843248

jlmorgado

---

### Post by kerry_s on 2007-01-10
In linux unused ram is wasted ram. Most things will load into memory so its faster, it will stay there till something else needs the ram, then it will be pushed off to swap & finally back to ram when needed again. Flash ram is faster than disk cause theres no moving parts so you get less ware & tare on your hardware. I also have 1 gig of ram & leave my computer on for months at a time and it will always stay responsive and fast because most of the apps i use is in ram already. If you want to clear the ram out just reboot.

Okay i type slow :)

---

### Post by az on 2007-01-10
> **jlmorgado said:**
> :)

Thanks for the fast reply. Ok, I understand that, but keeping almost 800MB in cache, for a whole day, when the machine is really not doing nothing... I know that it is impossible for the kernel to know if the things in cache will be used in the next minute, hour or day, but keeping all that amount of memory occupied for that long...



...what?

It's the way linux handles memory.  Keeping more memory free, or freeing up some memory yourself will not make your computer go any faster.   Just the opposite.  

Using all your ram is a good thing.

---

### Post by jlmorgado on 2007-01-10
Thanks to both of you...

I really understand what you're saying, but it's quite unconfortable to see all of my RAM being used :)

Thanks again

jlmorgado

---

### Post by rattking on 2007-01-10
Hi
if you are having problems with to much disc swapping and not enough cache being freed 
then you should look into swappiness set in
/proc/sys/vm/swappiness

here is a descent FAQ about it
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Swappiness_.282.6_kernels.29](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Swappiness_.282.6_kernels.29)

---

