---
title: "Weird memory usage problem"
date: 2007-06-13
forum: General Help
---

### Post by barthed on 2007-06-13
Before giving more details, the general question behind this post is: is there a reason why total memory usage (reported by top or free -o) cannot be explained by the processes’ memory usage (as reported by top or ps)?

I installed Ubuntu 7.04 server edition on a new computer (Pentium D with 1GB of RAM) along with these packages:

- ssh
- unison (file synchronizer)
- truecrypt (encryption.. had to compile from source)
- kde-core (but removed every startup scripts in rc2.d and rc3.d)
- vncserver (to remotely access kde when needed)

When I boot my machine, memory usage is around ~42MB.

The problem is that if I use any programs for a while, memory goes up and never gets back to a reasonable level. For example, if I start vncserver and kde, use it for a while and then stop them (all processes are killed), memory usage is still ~400MB.

A worse scenario is when I mount a truecrypt volume and then use unison to synchronize my windows machine with my ubuntu server. During synchronization, memory peaks at ~890MB and even after synchronization is over (and unison process is killed), memory usage stays at that level. To make a test, I unmounted my truecrypt volume, but still, memory usage was at ~515MB (and all processes related to truecrypt had been killed).

When I use top or ps to profile memory, I cannot find a single process that uses more than 3MB and I have *only* 57 processes (2 running, 55 sleeping). If I add the numbers in the %MEM column of top, it does not get higher than 2%!

I ran memtest86 for two hours and no error was detected (still, I know there is a slight chance that this might be hardware related).

Finally, I also did another test: I ran kde + java + eclipse + a lot of other applications until memory was at full capacity to see if swap memory would be used which was the case. 

Is there something I can do? Where should I look to find the *thing* that is taking most of the memory?

Thanks,
Bart

---

### Post by barthed on 2007-06-13
Ok, someone pointed free -m to me and I found that most of the memory is actually cached, a concept that I did not know anything about!

I'll read more about that...

---

### Post by shae on 2007-06-13
Memory management in linux is different.  When ram is avaliable, it uses it to cache previously opened programs for faster access.  If some other program needs to use the ram, the cache and buffers will be the first thing to be forced into swapspace.

---

