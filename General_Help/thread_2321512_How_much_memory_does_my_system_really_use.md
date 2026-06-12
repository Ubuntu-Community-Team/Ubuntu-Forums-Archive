---
title: "How much memory does my system really use?"
date: 2016-04-22
forum: General Help
---

### Post by lieven-debels on 2016-04-22
I use three methods to monitor memory usage:

1. the following terminal command:
```
free -m
```

2. conky

3. xmobar

I ran them all at the same time, and assumed the output of the three methods would be the same.
Wrong! They're not even close, as shown by the figures below.

The output of free -m shows my system is using 493 MB of RAM.
The output of conky shows my system is using 655 MB of RAM.
The output of xmobar shows my system is using 696 MB of RAM.

 Am I doing something wrong? Which method is accurate?
 I'm using Ubuntu 16.04 LTS.

---

### Post by DuckHook on 2016-04-22
I am not familiar with xmobar so can only comment on the first two. Measuring memory usage is a vague and ambiguous undertaking, especially with Conky scripts, which can be measuring just about anything. Are the units MB or MiB? Is cached memory being included (the system gives up such memory when needed, so is it committed memory or not)? Generally speaking, *free* gives the best reading because it is common across all systems. But it includes cache memory that must be backed out to give you a "proper" number.

---

### Post by Rocky_Bennett on 2016-04-22
Looks to me like those three numbers are actually quite close to each other.

---

### Post by lieven-debels on 2016-04-23
Well, this is the output of free -m at the moment:

                    ```
            total        used        free      shared     buff/cache   available
Mem:         7845         277        7197         95          370         7415
Swap:        5721           0        5721
```

So i would assume it's using 277 MB of RAM at the moment.

I assume when I put in ~/.conkyrc the variable $mem it should give the same reading, but apparently it does not.

@Rocky_Bennett: I won't consider a 200 MB difference between one method and another quite close, if it was 20 MB, I probably would.

---

### Post by mcduck on 2016-04-23
I'm not sure what's the default setting in Conky, but it has the option "*no_buffers yes*" which you can use to decide if the "*mem*" option for used RAM should include buffers&cache or not. Try with that one (or check if the difference in numbers is about the same as the "*buff/cache*" value reported by "*free*"

Edit: IN the "free" output from your last post, your applications and running services etc. are using 277MiB of memory. 97MiB of that amount is shared between multiple programs.  Then, additional 370MiB is used for various buffers (for example small data waiting to be written on the hard drive on one go rather than waking up a drive just for few small changes) and cache (data that was recently used, and while nothing is sayign it's needed any moe, it's kept around in RAM so if you eed it again soon, the system doesn't need to read if from your hard drive again)-

So, in a way, you are using total of 647MiB of memory. However only 277MiB is actually something that's *required* to be in RAM, the buffers/cache can be freed pretty much instantly if something needs more RAM, so in a way that still counts as available memory.

---

### Post by lieven-debels on 2016-04-23
Thanks for the responses so far.

I looked in the default settings of conky, and there is indeed an option defined no_buffers = true. If I set that to false, reported memory usage by conky approximately doubles. 
The weird thing is even with no_buffers = true, it' s still using 382 MB instead of the 277 MB reported by the free command. If I'm not mistaken, in older ubuntu versions, it seemed like it matched more.
I'll try again with 14.04, and see if the results are comparable to the figures am seeing here.

---

### Post by lieven-debels on 2016-04-23
Ok, so I booted from an Ubuntu 14.04.4 Live DVD and installed conky.
free -m output was 490 MB.
conky output was also 490 MB.

Then I booted from an Ubuntu 16.04 Live DVD and installed conky.
free -m output was 526 MB.
conky output was 1,03 GB.

So, the question is, why was conky output correct in 14.04, but isn't anymore in 16.04?
Is there anything I can do to get the conky output identical to the free -m output?

I want to use conky to display the memory usage on my desktop, but if it's output is way off it's not very interesting.
Also, I know I can get the free -m output by typing the following command in terminal: ```
free -m | cut -b 28-31 | head -n2 | tail -n1
```
But I don't know a good way to display this result every 3 seconds in the taskbar or on the desktop (like conky does)

Any ideas?

---

