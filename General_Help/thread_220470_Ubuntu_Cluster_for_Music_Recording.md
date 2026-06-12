---
title: "Ubuntu Cluster for Music Recording?"
date: 2006-07-21
forum: General Help
---

### Post by hermes980 on 2006-07-21
Hello all,

Before I depart on a crazy mission I need to consult on the following:

In music recording, power (cpu, ram, etc.) is the name of the game. So I am debating either getting a server board with 2 operton processors, running windows xp....or...call me crazy.....create a Linux cluster sharing cpu power to really have a super computer.

My question is:

-Since I use Audacity, would a cluster (load balancing) work.

-Since I have not used Linux yet (but programmed for years in Coldfusion) and built my own computers, would Ubuntu be the right linux program to use

-Have any of you used Linux or a Linux cluster for music recording and how did you set it up/what were the challenges, etc.

-Am I crazy for doing this and should I just stick to my dual operton system idea????

-If I am not crazy, how do I get started?

This is an open ended discussion, so lets have some fun!

---

### Post by pedwards on 2006-07-21
> **hermes980 said:**
> Hello all,



-Am I crazy for doing this 




yes,
i dont think its ever been done

---

### Post by buttari on 2006-07-21
> **hermes980 said:**
> Hello all,

Before I depart on a crazy mission I need to consult on the following:

In music recording, power (cpu, ram, etc.) is the name of the game. So I am debating either getting a server board with 2 operton processors, running windows xp....or...call me crazy.....create a Linux cluster sharing cpu power to really have a super computer.

My question is:

-Since I use Audacity, would a cluster (load balancing) work.

-Since I have not used Linux yet (but programmed for years in Coldfusion) and built my own computers, would Ubuntu be the right linux program to use

-Have any of you used Linux or a Linux cluster for music recording and how did you set it up/what were the challenges, etc.

-Am I crazy for doing this and should I just stick to my dual operton system idea????

-If I am not crazy, how do I get started?

This is an open ended discussion, so lets have some fun!

Simply it doesn't work. To use all the nodes in a cluster you need a parallel application and, as far as I know, Audacity is not. Not only parallel, but parallel with message passing (unless you use some sort of esoteric middleware like shmem). Multithreaded applications, in fact, will result in the execution of multiple threads on a single node of the cluster. Even using a dual core or dual proc (let's say smp in general) doesn't mean that your application goes faster. It does go faster only if, again, is parallelized (in the case of an smp multithreading goes fine). In case is not you can get advantage only by the fact that distinct processes can run on distinct processors/cores.
hope it helps

alfredo

---

### Post by hermes980 on 2006-07-21
Ummm, that would make sense. So when people use clustering it is for parallel processing, such as Database and splitting calculations? 

Is there another option to raise my CPU power or dedicate cpu power from other machines to run Audacity? (I would like to run it about 6 GHZ of speed)...ya, I am pushing it, I know.

---

### Post by hermes980 on 2006-07-21
Another forum just mentioned using an SMP Kernel. Is that what I am looking for, since I want to increase my overall processing power???:p

---

### Post by buttari on 2006-07-21
"do I have more power using a horse or 1000 chickens?"
"well, probably 1000 chickens but you have to convince them to push in the same direction."

Did you get it? If you have two (or more) processors you need an application that is capable of using them at the same time. Is you have such an application then, for example, on two processors you can expect to run at a speed than is 2 in a perfect world. In the real world you (almost) never get a perfect speedup because the two tasks that contribute to the application have to synchronize/communicate with each other. Parallel programming is a computer science subject per se and it's rather complex (it's my job, moreover :-) ). Anyway having an smp machine is still good for a reason: distinct processes may run on different processors. This means that, for example, if you run two instances of audacity you can have one on a processor and one on another. So, at the end, if you have a multiprocessor machine but not a parallel application you can increase the throughput of you system but not the performance.

Having an smp kernel is mandatory on smp architecture but it doesn't increase your power. the difference between a regular and an smp kernel is mostly in the fact that an smp kernel does the scheduling of processes (it decides which process has to run on which processor) and takes care of cache coherence and stuff like that. Anyway your non-parallel application is always going to run on one processos at a time.

if you have more questions I'll be glad to answer.

alfredo

---

### Post by christhemonkey on 2006-07-21
You say you have programmed for years?
You could try writing some sort of alsa/jack applicationi that utilises multiple CPUs.

Not being a programmer myself (yet!) i cant actually tell you whether it is physically possible/at all practical.

---

### Post by Boomy on 2006-07-21
Audacity is just an editor, not a multitracker, so out of curiousity why the need for all the CPU? Heck a Pentium II would provide more than enough power to record a pair of stereo tracks. 

I've done music production for years, and unfortunately  imho, nothing in Linux compares to the commercial apps for Windows and Mac. Also, a dual opteron has alot of processing power. My AthlonXP 3200 has been pretty good to me, even with 30 plus tracks and probably 30 or more plugins going. I have rarely maxed it out.

---

### Post by skirkpatrick on 2006-07-21
A dual-core processor would do you some good.  You run Audacity on the 2nd core and everything else on the 1st one.  When you hear about video rendering programs (like Cinelerra) running on a server farm, the software was created to hand off bits of the processing to other computers.  I would assume you'd get better performance with multi-track audio hardware.

---

### Post by buttari on 2006-07-21
> **skirkpatrick said:**
> A dual-core processor would do you some good.  You run Audacity on the 2nd core and everything else on the 1st one.  When you hear about video rendering programs (like Cinelerra) running on a server farm, the software was created to hand off bits of the processing to other computers.  I would assume you'd get better performance with multi-track audio hardware.

That's correct except for the fact that you cannot choose which program is running on which core unless you hack the linux kernel. The kernel tries to exploit processor affinity but you have no guarantee that your process will always stay on the same processor. Still it helps quite a lot. don't expect to go twice as fast.

alfredo

---

### Post by hermes980 on 2006-07-22
Thank all of you. I have now built a 50 machine cluster using dual core 2.5 Opterons operating at 3tflops with 400GB of Ram, and you should see how fast Notepad works. (just kidding :p )

Seriously though, all of your comments have been very helpful and satisified my intellectual curiousity while putting me on the right track! 

Regards!!!

---

