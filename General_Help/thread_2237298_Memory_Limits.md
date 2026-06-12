---
title: "Memory Limits"
date: 2014-08-01
forum: General Help
---

### Post by anon_private on 2014-08-01
I have noticed that Ubuntu tends to freeze, as does the system, when about 80% of the memory is used. Is this normal, rather than at 100%?

Is there a typical memory useage that one should aim for, that is, if one is using the right version of Ubuntu for the machine it will run  at around x% memory at maximum useage.

Thanks

---

### Post by vasa1 on 2014-08-01
How much RAM do you have?

---

### Post by mcduck on 2014-08-01
...and how much swap do you have? What are you doing when Ubuntu freezes? There really shouldn't be any issue with suing 80% or more of memory, the only problems are caused if  you try to use more memory than you have (in which case things will slow down as the system starts moving things between the swap and RAM. Or if you don't have enough swap, you'll get error message about not being able to allocate the neeeded memory and whatever you tried to do will just fail).

---

### Post by anon_private on 2014-08-01
Well spotted.

I am running Ubuntu from a live pendrive and Swap is not available (System Monitor has the green dot visible).

I can't remember the exact details of what I was doing at the time, probably surfing - having a number of browser windows open; Libre Office Writer running; System Monitor running; Home Folder open (probably a couple); copying files to another pendrive.

I noticed the memory at ca. 80% usage before freezing.

I have checked the memory recently with Memtest86 for about 8hrs (17 Passes, no errors).

As a matter of interest, if I install Ubuntu what difference would a Swap file make, I assume that I would have to create this file?

Should performance degrade as memory usage increases?

Best wishes.

A

---

### Post by mcduck on 2014-08-01
Having a swap partition (or file) allows the system to continue working even when it needs more memory than you have RAM available. The performance will of course suffer if the system needs to use the swap (accessing data from hard drive is considerably slower than accessing it from RAM), but it's still better option than not being able to work at all.

So it's not a question of performance degrading in linear way as memory usage increases, it's a hard limit at the point when memory usage exceeds the available RAM.

Swap is also used for other purposes, Linux kernel uses it to test if some cached data is till needed or if it could be discarded completely, by moving the old possibly-useless data to swap for a while and discarding it if it isn't used in a certain amount of time. (This way of using swap space is different from the actual swapping, and doesn't cause any performance issues, it's just a way for managing the memory usage better). And swap space at least the same size as your installed RAM is also required if you want to hibernate the computer.

---

### Post by 3rdalbum on 2014-08-01
> **anon_private said:**
> 
I have checked the memory recently with Memtest86 for about 8hrs (17 Passes, no errors).


Doesn't mean anything, unfortunately. I've had freezes, ran Memtest for 8 hours, no errors, took out one of my RAM sticks and the system became stable. It has been stable ever since, with different RAM sticks of course!

Your problem definitely sounds like bad RAM to me. Especially when you said about copying files - that's one of the things that uses a lot of RAM and if the data gets corrupted in RAM your kernel will panic. My freezes also had a tendency of happening while copying large files so I can testify to that.

80% RAM use can't, by itself, cause a freeze. Even 100% RAM use is not supposed to cause freezes. If the kernel runs low on memory it will start the Out-Of-Memory-Killer to quit your programs and free up RAM. Never tested it myself, but I've certainly skirted close to the edge of available RAM before now.

---

### Post by anon_private on 2014-08-01
> **3rdalbum said:**
> Doesn't mean anything, unfortunately. I've had freezes, ran Memtest for 8 hours, no errors, took out one of my RAM sticks and the system became stable. It has been stable ever since, with different RAM sticks of course!

Your problem definitely sounds like bad RAM to me. Especially when you said about copying files - that's one of the things that uses a lot of RAM and if the data gets corrupted in RAM your kernel will panic. My freezes also had a tendency of happening while copying large files so I can testify to that.

80% RAM use can't, by itself, cause a freeze. Even 100% RAM use is not supposed to cause freezes. If the kernel runs low on memory it will start the Out-Of-Memory-Killer to quit your programs and free up RAM. Never tested it myself, but I've certainly skirted close to the edge of available RAM before now.

My freezing was not associated with copying rather small files (in my case), it was just one of the activities I was involved in when freezing occurred.

I have another programme for checking RAM which I will try.

---

### Post by buzzingrobot on 2014-08-01
Swap is a partition on Linux, not a file as on Windows.

If 'X' percent of RAM is allocated and something requests a new allocation of RAM that cannot be met -- current allocations plus new allocation request = greater than available RAM -- then the system will start killing off processes or potentially halt if swap is not available or start using swap if it is.

Swap is also mandatory for hibernation.

---

### Post by anon_private on 2014-08-01
> **buzzingrobot said:**
> Swap is a partition on Linux, not a file as on Windows.

If 'X' percent of RAM is allocated and something requests a new allocation of RAM that cannot be met -- current allocations plus new allocation request = greater than available RAM -- then the system will start killing off processes or potentially halt if swap is not available or start using swap if it is.

Swap is also mandatory for hibernation.

Would these requests be reflected in System Monitor, that is recorded as 100% Memory, even though the true required figure is greater.

---

### Post by buzzingrobot on 2014-08-01
> **anon_private said:**
> Would these requests be reflected in System Monitor, that is recorded as 100% Memory, even though the true required figure is greater.

Don't know; don't know how System Monitor measures and displays memory. I don't know, either,  how it deals with memory temporarily swapped out.

---

### Post by mcduck on 2014-08-01
System Monitor won't tell you directly if you are trying to use more RAM than what you have, it only displays what's *actually used* (and you can't use more than 100%). If you have swap, then increase in swap usage is of course a good sign that you are trying to do something that requires more memory than you have. Otherwise you'd just notice it from programs being closed or crashing, error messages about not being able to allocate required memory, or through log files.

The point here is that you can't use more memory than you have, period. Any application trying to request more than what can be assigned (either directly using RAM, or by swapping) will fail immediately, there's no system for keeping the app running and making a note that it actually needs more memory to run.

---

### Post by obake2 on 2014-08-02
> **anon_private said:**
> Well spotted.

I am running Ubuntu from a live pendrive and Swap is not available (System Monitor has the green dot visible).



Unless you did not install SWAP, most likely you are facing a certain bug that is affecting ubuntu 14.04 as [described here]("http://ubuntuforums.org/showthread.php?t=2221067"). The solution can be [found here]("http://ubuntuforums.org/showthread.php?t=2224129").


EDIT: Oh.You are running Ubuntu in a Live session? Never mind then. Still keep this in handy if you decide to install Ubuntu.

---

