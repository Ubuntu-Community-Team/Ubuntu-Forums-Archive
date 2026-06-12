---
title: "Out of Memory error in Matlab, though Swap seems to work"
date: 2006-11-19
forum: General Help
---

### Post by FrankL on 2006-11-19
Hello all,

I did an upgrade to Edgy some time ago. I noticed my swap didn't work, so I edited the fstab and used swapon to turn swap on. That seems to work, looking at:

frank@frank-laptop:~$ sudo swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       6144852 0       -1

But when I try to run a program in Matlab which previously always worked, I get an out of memory error. 

Can is be that my swap space still doesn't work? Should the priority be -1? I read somewhere it means it is activated, so I hope it is right. Changing it didn't help though. But it is striking IMO that no swap is used at all at any time, so I think the problem is indeed there.

I hope someone can help me,

thanks in advance,

Frank

---

### Post by lloyd_b on 2006-11-19
Just for verification, in a terminal window type "free".  This will give you a good breakdown of memory, and should tell you exactly how much swap space you have available (as well as how much is being used).

That priority of "-1" is normal.

Just out of curiosity, how much memory do you have, and how much of it is free after the system boots ("free" will tell you this).  The fact that you're using 0 swap generally means that you have so much physical RAM that Linux doesn't need to use any swap.

I'm not familiar with Matlab, but my initial guess is that the problem is in it's configuration. 

Lloyd B.

---

### Post by FrankL on 2006-11-19
Thanks for your response. Free gives the following:

frank@frank-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1035528     869136     166392          0      42760     374196
-/+ buffers/cache:     452180     583348
Swap:      6144852          0    6144852

I've got 1024 MB ram, should be enough I guess. But matlab doesn't think the ram, nor the swap, is enough...

---

### Post by lloyd_b on 2006-11-19
> total used free shared buffers cached
Mem: 1035528 869136 166392 0 42760 374196
-/+ buffers/cache: 452180 583348
Swap: 6144852 0 6144852

Is Matlab a Windows program?  If so, how are you running it?

That "452180" figure for memory used after buffers/cache has been subtracted is extremely high for a pure Linux system - you generally only see that kind of memory usage if the machine is very heavily loaded (running many tasks), or if there's an emulator running that's grabbing a big chunk of memory.

If you are running an Windows emulator, then the problem is in the emulator's configuration.

I don't see any problems with your memory usage (other than that high number), and swap looks fine.  You just have so much physical RAM that Linux doesn't feel the need to swap anything.

Lloyd B.

---

### Post by FrankL on 2006-11-19
Thanks for clarifying the statistics. There is also a linux version of matlab and that's the one I'm using. The big memory usage is probably due to the fact the I am testing quite big neural networks at the moment.

But I figured out what the problem was: it was a error in my own code, for which matlab gave a strange error. Probably it was pure coincidence that I had swap problems at the same time.

Thanks for the help anyway!

---

