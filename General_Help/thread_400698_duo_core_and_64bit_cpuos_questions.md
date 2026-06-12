---
title: "duo core and 64bit cpu/os questions"
date: 2007-04-03
forum: General Help
---

### Post by nonewmsgs on 2007-04-03
are core 2 duo are 64bit?
without a 64bit OS can you run 64bit software?
without a 64bit OS is there a performance difference

duo core chips...those are almost like having 2 CPUs, right? i noticed that 2.4ghz duocore chips are around the top of my price range, but my old cpu 2.4ghz single core is still kicking pretty well.

ive read a lot of material on it and have ended up more confused than ever.  i respect you guys, so give it to me straight.

---

### Post by dfreer on 2007-04-03
I can't speak for the entire core 2 duo line, but my (t7200) core 2 duo is 64-bit. From what I understand of it, in general core duos = 2 cores and core 2 duos = 2 cores and 64-bit.
It is almost like having 2 CPUS, in fact I notice I can run VMWare and it will exclusively use one core while my OS is using the other core, which is rather nice. I've never been sure of the naming convention, whether a 2.00 ghz dual core is equal to 2x2.00Ghz processors (4 Ghz all together) or 2x1Ghz (2 Ghz in total). But I'm sure someone else here does.

---

### Post by dfreer on 2007-04-03
> without a 64bit OS can you run 64bit software?
no. but a 64-bit OS can run 32-bit software.

> without a 64bit OS is there a performance difference
From what I hear over at the x86_64 bit forum, a 64-bit processor with a 32-bit OS can lead to *slight* performance decrease and possibly incompatibility, although that could be FUD in reverse for all I know. Best to ask this question in that forum... :D

---

### Post by nonewmsgs on 2007-04-03
FUD? is that  like placebo effect?  and i dont want to be doubleposting so can someone port this over to 64bit?

---

### Post by Drunner611 on 2007-04-03
> **dfreer said:**
> I can't speak for the entire core 2 duo line, but my (t7200) core 2 duo is 64-bit. From what I understand of it, in general core duos = 2 cores and core 2 duos = 2 cores and 64-bit.
It is almost like having 2 CPUS, in fact I notice I can run VMWare and it will exclusively use one core while my OS is using the other core, which is rather nice. I've never been sure of the naming convention, whether a 2.00 ghz dual core is equal to 2x2.00Ghz processors (4 Ghz all together) or 2x1Ghz (2 Ghz in total). But I'm sure someone else here does.

Not Quite.  Core Duo's are simply single core, 64-bit processors.  Core 2 Duo's are 2 core 64bit procs.  As far as the ghz goes.  A 2.00 ghz dual core proc means there are two cores, both running at 2 ghz.  Now, they aren't as efficient as a single 4 ghz proc, but those don't exist anyway.  

dfreer has got all the 64 bit details down.  A 64 bit processor can run a 32 bit and 64 bit OS.  You cannot run a 64 bit program in a 32 bit OS no matter what the processor.  There is a slight performance increase, depending on the application you are running.

---

### Post by marcus16 on 2007-04-03
> **Drunner611 said:**
> Not Quite.  Core Duo's are simply single core, 64-bit processors.  Core 2 Duo's are 2 core 64bit procs.  As far as the ghz goes.  A 2.00 ghz dual core proc means there are two cores, both running at 2 ghz.  Now, they aren't as efficient as a single 4 ghz proc, but those don't exist anyway.  

dfreer has got all the 64 bit details down.  A 64 bit processor can run a 32 bit and 64 bit OS.  You cannot run a 64 bit program in a 32 bit OS no matter what the processor.  There is a slight performance increase, depending on the application you are running.

Nope, all Core Duos are dual cores.
But only Duo 2 are 64 bit.

Edit: Intel Core Solo are only single core.

And a 2GHz CPU would have advantages over a 4GHz single core. It has the ability to execute multiple things at once.

---

### Post by dfreer on 2007-04-03
> FUD? is that like placebo effect?
FUD. Fear. Uncertainty. Doubt.
[http://en.wikipedia.org/wiki/Fear%2C_uncertainty_and_doubt](http://en.wikipedia.org/wiki/Fear%2C_uncertainty_and_doubt)
The 64-bit forum has a lot of threads covering this (seems like there is a new one every day), you will see a lot of posts recommending that 64-bit users should give up using a 64-bit OS and go back to 32-bit, mainly because of the issues of Flash, Java, Wine and a few other programs not having a 64-bit port (although it is possible and, dare I say, *easy* to get the 32-bit versions of these programs working while running 64-bit Ubuntu).
FUD in reverse is something I just came up with to describe how die-hard 64-bit fans seem to claim that running 32-bit OS on a 64-bit processor will cause performance loss and hardware incompatibility. 
Although I'm sure there are merits to both sides claims, I think it's simply a matter of choice of what you want to run and what works best for you. Read up on some of the threads and ask more questions, it's what we are here for :D
. 
EDIT:
> As far as the ghz goes. A 2.00 ghz dual core proc means there are two cores, both running at 2 ghz. Now, they aren't as efficient as a single 4 ghz proc, but those don't exist anyway.
thanks for the info! I have a question, but keep in mind I'm speaking in generalities, I know the kernel shares processor time etc. 
Now, let's say I'm running an application on a dual core 2ghz machine. Can my program run at the full potential 4 ghz (both cores simultaneously), or am I limited to 2 ghz per process? Like I would only be able to run 2 programs using 2 ghz (1 core) each, but not 1 program using both cores? just curious, thanks!

---

### Post by Drunner611 on 2007-04-03
> **marcus16 said:**
> Nope, all Core Duos are dual cores.
But only Duo 2 are 64 bit.

Edit: Intel Core Solo are only single core.

And a 2GHz CPU would have advantages over a 4GHz single core. It has the ability to execute multiple things at once.

Doh, you got me.  Lol.  I don't know what I was thinking. ](*,)

---

### Post by marcus16 on 2007-04-04
> **dfreer said:**
> thanks for the info! I have a question, but keep in mind I'm speaking in generalities, I know the kernel shares processor time etc. 
Now, let's say I'm running an application on a dual core 2ghz machine. Can my program run at the full potential 4 ghz (both cores simultaneously), or am I limited to 2 ghz per process? Like I would only be able to run 2 programs using 2 ghz (1 core) each, but not 1 program using both cores? just curious, thanks!

It's not as black and white as 2 GHz per process. But no they don't combine to form a 4 GHz core.
But that's not even important. That's why the new Intel chips have a lower clock speed then the  Pentium 4's, but are vastly better. Even without the second core.

---

