---
title: "dual core jobs question"
date: 2007-09-18
forum: General Help
---

### Post by sblanzio on 2007-09-18
Hi!

I would like to know if it is possible to assign a process to a particular cpu core.
Does exist a command to decide that?

I am thinking about something like "nice" command but referred to cpu cores.

thanks everybody!
bye!

---

### Post by dixonp on 2007-09-18
Yes, with "numactl --physcpubind". **But** the kernel process scheduler is already extremely good at assigning CPUs/cores to processes. I cannot stress this enough. 99.9% of desktop users _will_ either degrade performance or bring no improvement at all by using numactl. This command is only useful in very specific cases. E.g. if your machine has a non-uniform memory layout, such as a 2P Opteron server.

For example my (old) Opteron workstation has 1GB on CPU0 and no memory on CPU1, so when 2 or more CPU intensive programs are being run, the kernel kind of randomly assign them to the CPUs, but I have the possibility to tie one of them to CPU0 to give it access to lower latency memory.

---

### Post by sblanzio on 2007-09-18
Thank you for your answer!

I've read somewhere that if the software is not designed for dual-core, our cpu are not able to manage correctly their jobs... and they actually just work alternatively, with a significant reduction of performance.

In fact, most of the times, under heavy jobs, I can see just one core very busy, and the other one is almost at 0%, and then sometimes (without any apparent reason) they exchange their percentual datas, the first becoming to 0% and the other one gets busy, but they almost never seem to work together.

So I thought it could be helpful to assign manually some tasks...

Where do I mistake?
why do they exchange their percentuals sometimes?

thanks again,
sblanzio

---

### Post by dixonp on 2007-09-19
If the software is not multithreaded, a dual-core cpu will *not* slow it down. The kernel will simply schedule the software to run on one core, and perfectly normal operational conditions will cause it to move from one core to another from time to time.

You really shouldn't worry about seeing this happening. This is perfectly normal. For your information, the kernel schedules "time slots" (typically a few millisecond each) during which it executes a single process on a given core. And hundreds/thousands of times per second, the kernel looks at the process queue (the technical term is "task queue") and may decide to execute other things that need to be executed. So for example even a small spike of cpu utilization that you wouldn't see (say < 1 ms) on 1 core by a random process is sufficient to make the kernel decide that your process should be moved to the other core.

The decision of which application to execute on which core/processor is made by the process scheduler. This is an area of the kernel that is very well studied. If you want to see the sort of technical studies that kernel developers do to write efficient process schedulers, you can look for example at this very recent discussion thread about the "CFS" scheduler, that is included in the latest kernel versions: [http://kerneltrap.org/Linux/Additional_CFS_Benchmarks](http://kerneltrap.org/Linux/Additional_CFS_Benchmarks)

---

