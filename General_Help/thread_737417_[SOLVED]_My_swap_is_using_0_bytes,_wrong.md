---
title: "[SOLVED] My swap is using 0 bytes, wrong?"
date: 2008-03-27
forum: General Help
---

### Post by mkarnicki on 2008-03-27
Hi there,

The System monitor (attached) shows swap is using 0 bytes. Is this OK? I thought swap is used extensively, or at least just IS used. And mine looks like not used at all.. The screen shoot was taken with firefox, thunderbird, skype, and some more memory-light stuff. Explanation appreciated.

---

### Post by prshah on 2008-03-27
> **mkarnicki said:**
> Hi there,

The System monitor (attached) shows swap is using 0 bytes. Is this OK? I thought swap is used extensively, or at least just IS used. And mine looks like not used at all.. The screen shoot was taken with firefox, thunderbird, skype, and some more memory-light stuff. Explanation appreciated.

With 2Gb of RAM, I wouldn't wonder that it's not being used.

It looks OK, mounted and everything. If your swap was not mounted, it wouldn't show 3+Gb as swap space.

---

### Post by wolfen69 on 2008-03-27
swap is only used if/when you get low on memory. you have 1.8gb of memory, which is more than enough for everyday stuff. it is nothing to worry about. i have 2gb ram and never see any swap usage.

---

### Post by seeker1458 on 2008-03-27
My understanding is that the swap is used to releave virtual memory.  You've got almost 2GB and are only using 27% with the applications you listed running.  There is no need to load anything to swap b/c you've got roughly 75% or your RAM (which is much faster) free.  I was told if your system has more than say, 1GB of RAM for linux, you don't even need to create a partition for swap. Im running gutsy on a macbook w/ a 2.16 C2D, 2GB of 667, and I don't have a swap.  My system runs fine.

---

### Post by Lord Illidan on 2008-03-27
Try maximizing your RAM (run a couple of games, load up 10 instances of Office), and see what happens. Swap is a last resort, remember that it's extremely slow when compared to RAM.

---

### Post by Battie on 2008-03-27
Thanks for this information.  I was a little confused too.

So this is much different than Windows, right?  It seems to always be using its page file, even on systems with plenty of RAM.  Why is this?

---

### Post by mkarnicki on 2008-03-27
Thank you all for your posts ^_^ I really like it about ubuntu community, that it's so eager to help. So I guess this explains everything. I may load many apps to see, if I use some of my swap, indeed. Just for fun :) Thanks again.

**@Battie** 1st ubuntu seems to be lighter than windows (ofcourse depending on the OS configuration) 2nd windows is stupid ^-^ muhuhuhuh that's why it uses page file all the time ^ ^ But  jokes aside, I think windows leaves the pagefile untouched, if not needed, therefore it doesn't clear up everytime you shutdown, if not configured otherwise. Therefore it may seem, that it's being used all the time, but it may be just some old crap sitting there. But I can be wrong.

---

### Post by mkarnicki on 2008-03-27
I'm not editing above's to let you know... that trying to use so much ram, to make use of swap, with 2 GB ram, is ridiculous :D I've loaded like... many, MANY apps, like.. 15 including gimp, movies, e-mail clients, firefox, communicators, and some more.. mixed with transparency to make some load on the system, and.. I got up to <700 MB RAM used, AMD Turion cores 14% and 12% used and.... my laptop used up to 554 KB swap hahahahah... finally, it jumped to 22 megs. That was an interesting research ;) At least fun. Cheers (btw take that as research, not as a show-off, please)

---

### Post by dimafal on 2008-05-21
> **mkarnicki said:**
> I'm not editing above's to let you know... that trying to use so much ram, to make use of swap, with 2 GB ram, is ridiculous :D I've loaded like... many, MANY apps, like.. 15 including gimp, movies, e-mail clients, firefox, communicators, and some more.. mixed with transparency to make some load on the system, and.. I got up to <700 MB RAM used, AMD Turion cores 14% and 12% used and.... my laptop used up to 554 KB swap hahahahah... finally, it jumped to 22 megs. That was an interesting research ;) At least fun. Cheers (btw take that as research, not as a show-off, please)

As for me, it is simple to fill all 2GB memory: try to start any Virtual Machine with 1GB in it, and you can`t work without swap.

---

### Post by xeth_delta on 2008-05-21
> **Battie said:**
> Thanks for this information.  I was a little confused too.

So this is much different than Windows, right?  It seems to always be using its page file, even on systems with plenty of RAM.  Why is this?

As other users have stated, RAM memory is way way much faster than the HDD could be. Hence, in Linux, if there is no need to use swap (which is HDD based), it will not be used. Why make the system run slower, after all, when there is enough RAM.

A little off-topic. Linux will normally use RAM as efficiently as possible. What I mean is, that the amound that is not allocated or used by programs, will be used for buffers and cache, in order to improve responsiveness of the system. For a quick overview on how much is allocated to buffers/cache you can open a terminal and run:
```
free -m
```
It will tell you in MB (the -m option) how much memory is used (per total) and how much of it is going to buffers/cache.

---

### Post by wootah on 2008-05-21
> **xeth_delta said:**
> 
```
free -m
```
It will tell you in MB (the -m option) How much memory is used (per total) and how much of it is going to buffers/cache.

```

tripp@eclipse-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        968         42          0        294        224
-/+ buffers/cache:        449        561
Swap:         1819         34       1785
tripp@eclipse-desktop:~$

```
So does this mean that Linux is grabbing basically all of the memory, but reserving it for fast access (buffers/cache)? When a program needs a chunk of memory, does it just get released from one of the two (+ maybe swap) ?

---

### Post by xeth_delta on 2008-05-21
> **wootah said:**
> ```

tripp@eclipse-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        968         42          0        294        224
-/+ buffers/cache:        449        561
Swap:         1819         34       1785
tripp@eclipse-desktop:~$

```
So does this mean that Linux is grabbing basically all of the memory, but reserving it for fast access (buffers/cache)? When a program needs a chunk of memory, does it just get released from one of the two (+ maybe swap) ?

Indeed, it uses all the free memory for fast access. It gets released when a program needs it, AFAIK. Swap, because it is really slow, is used only as a last resort, when physical memory is full.

---

### Post by mkarnicki on 2008-05-21
Interesting, thanks for your tips :)

---

