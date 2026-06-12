---
title: "Ubuntu 13.10 memory thrashing"
date: 2014-08-29
forum: General Help
---

### Post by mgoldenbe on 2014-08-29
I have problems with the computer slowing down, and sometimes even freezing completely (mouse not moving) under Ubuntu 13.10 (the fan working all the time).  I believe that the issue is related by memory consumption by the programs, notably the web browsers. When I open Firefox with only one tab (gmail), it already consumes more than a Gigabyte of virtual memory (shown by top). I tried the Midori browser and that one started up consuming 2.5 GB! Then I installed Chromium. While installing it, I noticed that the software center's consumption peaked >2 GB! All these seem to be abnormal.   Another abnormal behavior I observed was that a CPU-intensive process (I wrote the program, so I know that it's CPU-intensive) slowed down to using about 1% of CPU, while there were no other processes consuming CPU. This phenomenon happened only once so far, so I cannot re-produce it.  I will very much appreciate any help in resroring my ability to work effectively under Ubuntu. Thanks!  P.S. The symptoms do not show under Windows, so I don't believe that this is due to a hardware issue. (Just in case, I ran memory and disk checks, which did not reveal any problems)

---

### Post by claracc on 2014-08-29
I don't know if it is related (I think it is), you are runing an end of life support ubuntu, the date was july 17 for 13.10. So I recommend you to install a supported one: 12.04 or 14.04.

Also it would be good you give us your hardware specs: cpu, ram, harddrive and graphics card and an example of top command when runing some browser.

---

### Post by Impavidus on 2014-08-29
My Firefox (three tabs open) consumes 1,138,688 kiB virtual, total memory used is 1,132,116 kiB, which is less. It's sometimes a bit tricky to see what is actually indicated by memory usage. Memory mapped files with disk backing, allocated but unused memory, cache, memory shared by multiple applications (using shared libraries), it all influences how we can count memory. In different columns top counts it in different ways. How much percent memory usage is given by top?

What are the specs of your system? The fact that Windows doesn't show problems doesn't completely rule out a hardware issue (Windows manages memory in a different way and may never touch the bad part), but if you checked the memory it's probably OK.

Note that Ubuntu 13.10 is obsolete. Maybe you want a clean install of 14.04 LTS, wich may at the same time solve your problem.

---

### Post by mgoldenbe on 2014-09-03
Thank you for the replies. I do not switch to 14.04 yet, because that would require me to install all the needed for my work software packages and take me several days, which I currently cannot afford. I very much appreciate your willingness to help despite my version being obsolete. 

I am running Acer Aspire 7750ZG laptop with Intel Core B940 CPU and 3 GB DDR3 memory. Top shows that firefox uses 17% of memory. Also, it shows:

KiB Mem:   2865992 total,  2500004 used,   365988 free,    16584 buffers
KiB Swap:  2992124 total,   253956 used,  2738168 free,  1076088 cached

I find this really strange given that I am not running any programs that should use a lot of memory (currently, it's only firefox with 4 tabs without flash or any fancy stuff like that and with NoScript enabled, codeblocks with a rather small project open, emacs, pdf viewer with a really small document open and a few terminal windows).

---

### Post by mcduck on 2014-09-03
Don't look at the "virtual memory" line, that includes a lot more than just the amount of RAM a program uses. It's the *resident memory* you should be looking at.

What does "free -m" say? (read the "-/+ buffers/cache"-line)

Either way, you do seem to be using some swap which is a sign of running out of available RAM, however based on your last post it's not Firefox that's causing any issues (browsers with even a few tabs open can eaily use lots of memory, and 17% out of 3GB is really nothing)7

edit: just to add a bit of explanation, "virtual memory" means the whole address space of data a process has access to. So it doesn't mean it's actually *using* all that data, or even that all that data would ever exist in RAM, it's simply all the data in RAM, on your hard drives and other devices etc. that the process has reported it *might* want to read at some point and therefore needs to have an address. And it even includes address spaces the process has reserved in case it will need to add more data at some point, but which aren't even pointing anywhere yet. So definitely not the value to look at when trying to determine how much RAM something is using... :)

---

