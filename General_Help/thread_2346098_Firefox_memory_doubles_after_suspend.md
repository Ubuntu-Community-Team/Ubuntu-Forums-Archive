---
title: "Firefox memory doubles after suspend"
date: 2016-12-11
forum: General Help
---

### Post by mistcloud-misty on 2016-12-11
Hello. Perhaps it may be my poor laptop practices that cause it, but I tend to leave Firefox open when using suspend (just on my email and maybe whatever I was previously working on for my classes), which I have been doing for a long time... however, I noticed the other day when looking at inxi outputs that I was using 6.8 GB out of 8 in memory... checked resources and firefox, on an ordinary HTML text page, was at 3.5 GB of memory. Restarted it, went to the same page, and it was back down to 250 MB. 

So I've been checking it recently, and after a single successful suspend this morning firefox memory doubled from 250 to 500. Second suspend, it went up to 950. 

Is there a way to prevent this or should I just close all my work before suspending? I don't recall this ever being a problem before, honestly. I do have adblock plus installed as my only additional extension. Any ideas?

---

### Post by DuckHook on 2016-12-12
*inxi* is a great little app but is designed to give you HW data and gives only a misleading single number for RAM usage. However, it is easy to get an overview of top-level memory allocation. The command:```
free -hwt
```…gives a breakdown of overall memory usage. I suggest running this every time after you suspend (with FF running) and piping the results to a text file with```
free -hwt >> ~/Desktop/memory_usage.txt
```The double greater signs are essential: single signs will replace the contents of the file rather than add to them. After a few repetitions, you can either post the resulting file back to this thread, or draw your own conclusions based on the following (note: due to security concerns, I do not use suspend, so what follows are just educated guesses):

I suspect that your system is behaving as it is supposed to, and the growing memory usage is merely iteratively increasing cache. As stated, this is just a guess. You must confirm it with the simple procedure above. If cache, then the OS will release such memory as and when it is needed.

Cache memory exists to speed up the user computing experience by putting recently used or often used content into RAM instead of drawing it from disk (which is generally hundreds of times slower) or downloading again from the internet. My suspicion is that, since the act of suspending does not actually shut the system down, the OS does not flush the cache. So every time you suspend, it places *all* memory content into RAM *including the current cache*, then treats that content as something recently accessed&#8213;which it therefore caches. The next time you suspend, the whole cycle repeats itself, but now with all of the previous cached content re-cached. I'm guessing this from the fact that your RAM usage roughly doubles with each iteration. I could easily be totally wrong&#8213;I'm not a kernel guru.

You might consider an experiment: with all important data backed up, and nothing important open except FF, suspend and resume a few times until your RAM is maxed out (observe with *free* command). Then continue doing so. If the problem is a memory leak, your next iteration should either crash your computer (it has no RAM left), or drastically slow it down if you have a swap in use (as memory is swapped out to disk). If, however, the system is just as responsive and your memory allocations don't change much, then the system is merely chucking out chunks of old cache to make room for new, and behaving as it should.

I will add one thing: while I do not think your laptop practices at all "poor", you may wish to consider the following:

[LIST=1]
[*]Suspended laptops are a known increased penetration risk for encrypted disks. This is because the computer is never really "shut down", so the encryption key remains active and therefore accessible to RAM sniffing kernel exploits. If your laptop is ever stolen while suspended, it is far easier for a bad guy to crack than a fully powered off machine. Of course, if you don't encrypt your data anyway, then this consideration is moot.
[*]Even simplistic security measures like locking upon suspending are sometimes broken with updates/regressions. This is a known issue. Example: [https://bugs.launchpad.net/linuxmint/+bug/1185681](https://bugs.launchpad.net/linuxmint/+bug/1185681)
[*]Against all of the above, millions of people suspend without a care in the world. Some get their laptops stolen and their personal info used against them. Most do not. Only you can decide where on the security versus convenience continuum you feel comfortable.
[/LIST]

---

