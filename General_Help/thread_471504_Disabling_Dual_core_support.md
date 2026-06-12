---
title: "Disabling Dual core support?"
date: 2007-06-12
forum: General Help
---

### Post by anaconda on 2007-06-12
I have an intel pentium 4 2,6GHz single core processor. But the generic kernel thinks that I have 2 processors. 

Is there any way I could disable the 2 core support? 

I have tried the boot time options "nosmp" and "maxcpus=0" but the machine wont boot at all if either of those is specified.

I know that if I change to the i386 kernel the machine will speed up and have only one processor, but is there any way to get the generic kernel to work?

arrgh annoying bug in the generic kernel  ;(

---

### Post by mcduck on 2007-06-12
> **anaconda said:**
> I have an intel pentium 4 2,6GHz single core processor. But the generic kernel thinks that I have 2 processors. 

Is there any way I could disable the 2 core support? 

I have tried the boot time options "nosmp" and "maxcpus=0" but the machine wont boot at all if either of those is specified.

I know that if I change to the i386 kernel the machine will speed up and have only one processor, but is there any way to get the generic kernel to work?

arrgh annoying bug in the generic kernel  ;(

It's not a bug, your CPU supports HyperThreading which makes single core CPU work (in some situations) like if it had 2 cores. It should in no way make your system any slower.

---

### Post by gerscht on 2007-06-12
If you really want to use just 'one', you should be able to disable multi threating in the BIOS.

---

### Post by anaconda on 2007-06-12
> **mcduck said:**
> It's not a bug, your CPU supports HyperThreading which makes single core CPU work (in some situations) like if it had 2 cores. It should in no way make your system any slower.

Hmm. That is intersting! Thanks for the info.

So it is normal that the 
more /proc/cpuinfo
and "system monitor"
will always show 2 processors?

---

### Post by mcduck on 2007-06-12
> **anaconda said:**
> Hmm. That is intersting! Thanks for the info.

So it is normal that the 
more /proc/cpuinfo
and "system monitor"
will always show 2 processors?

Yes, it's normal with your CPU.

The idea in HyperThreading is that the CPU is actually seen as 2 logical CPU's, while there really is just one actual core. Now, programs can be run on either one of these logical CPU's, while the the work assigned for both cores is actually done by the only physical core the CPU has. This way when a program running on logical CPU 1 stops to wait for some data from memory your CPU starts doing jobs assigned for the 2:nd logical CPU. This way your CPU time is used more efficiently as less CPU time is wasted while waiting for data.

So, while hyperthreading doesn't actually make your CPU multicore, it makes it use it's one core more efficiently.

[http://en.wikipedia.org/wiki/Hyperthreading]("http://en.wikipedia.org/wiki/Hyperthreading")

---

