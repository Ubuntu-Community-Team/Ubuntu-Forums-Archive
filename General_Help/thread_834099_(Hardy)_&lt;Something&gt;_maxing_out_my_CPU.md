---
title: "(Hardy) &lt;Something&gt; maxing out my CPU"
date: 2008-06-19
forum: General Help
---

### Post by Donalb on 2008-06-19
Hi all,
Ok,I've been using Ubuntu full time for about 2 months and loving it.
It's given new life to my 3 years old Dell Latitude D600, Penbium 1.7ghz with 1Gb ram. Ok, but I don't suspect a Hardware problem so I haven't posted in the Laptops forum... 

Anyway, using Hardy, auto updated to Kernel 2.6.24.18 about a few weeks ago. Sometime later (not sure, few days anyway)then I noticed my CPU starting to Max out to 100% intermittently.
Went back to starting on Kernel 2.6.24.16. Still the same problem.

Firefox is usually open when it happens and will often hang. Updated to FF3 from RC3 and FF beta 02 before that, with plenty of add-ons.
 
Howover closing FF doesn't usually release any resources. 
I usually have Thunderbird & Transmission also, with aMule open intermittently. Closing any  one of these or all of these doesn't free up the CPU (though I did notice closing FF last night had the effect, the only time).

If I was back on XP I'd suspect a virus or trojan from the intermittant behaviour . Not running any Anti-virus NOR firewall (yes stupid on the Firewall, I forgot until this post, will install Firestarter?)

Watching the System monitor no particular shows as using the whole CPU, but the resources page shows the CPU maxed.

Apart from installing a FireWall, any other suggestions?


Regards
Donal

---

### Post by argail1980 on 2008-06-19
open a terminal (somewhere in Applications -> accesoires)

and type

```
top
```

when that happens the next time. this shows you the processes that use most of the resources at the moment. you quit the program by hitting Q.


Also have a look at:
[http://ubuntutip.googlepages.com/bugsinubuntu]("http://ubuntutip.googlepages.com/bugsinubuntu")
there is something about a memory leakage in firefox 3.

---

### Post by bingoUV on 2008-06-19
1. No need to install any firewall.

2. When no process in particular is taking CPU time but CPU maxes out, this is a sure sign of high I/O activity. The first point in the link pointed out by argail1980 is what is most likely to help you.

---

### Post by scottywz on 2008-06-19
I'm having a similar problem.  I'm on an Acer Aspire 9500, 1.6 GHz Celeron M, 1.5 GB RAM, hardy, kernel 2.6.24-19 generic.  Right after I log in the CPU is almost at 100%, with an average 57% user and 28% system according to top.  No particular process is using this many resources at a given time.  Since it's right when I log in, maybe before then, I know it's not Firefox.

What could be causing this? :confused:

---

### Post by bingoUV on 2008-06-20
57% user means some processes are using the CPU. How long does it last? Check system monitor for longer, sort by CPU usage and see the process coming on top of the list.

---

