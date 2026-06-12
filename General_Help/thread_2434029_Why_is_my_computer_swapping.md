---
title: "Why is my computer swapping?"
date: 2019-12-29
forum: General Help
---

### Post by shmu26 on 2019-12-29
Kubuntu 19.10
I have a 2 GB swap partition, and 8 GB RAM.
I have swappiness set to 10.
The System Monitor shows I am using 4.9 GB out of 7.6 GB memory, and also shows that swap usage is 0.10 GB.
I know that's not a lot of swapping, but why is it happening at all? I thought that swappiness set to 10 means swap will only be used when free RAM goes under 10%?

---

### Post by crip720 on 2019-12-29
Think ubuntu uses swap most of the time.  Have 16GB memory, using about 45%, and 19% of 1.6GB swap.  My swap is set to whatever ubuntu decided.

---

### Post by CatKiller on 2019-12-29
It just means that at some point your system needed to allocate 6.9 GB rather than the 6.8 you had available. Since your cruising level is 5 GB, that's not a lot extra; opening something in the Gimp, or a heavy browser tab, or whatever, can do that extra bit.

It's not something to worry about. Processes say "I need this much memory for this thing I'm doing" and the system says, "OK, then, here you go" and everything ticks along fine. A little bit now-and-then so that nothing ever has to not be able to allocate memory is what swap is *for*.

I'm using the default swappiness of 60 and with 16 GB of RAM my swap never gets touched for any of the things I normally do, since my computer is much better at multitasking than I am. Fire up Minecraft, though, and I'm *very* happy that there's an extra safety level for whatever horrific thing Java is doing with memory until it gets round to garbage collection.

As I'm sure you know, you don't want to get into the situation that you're *running things* from swap (which would mean that you need more RAM), but having that little bit extra available for housekeeping is perfectly fine.

---

### Post by shmu26 on 2019-12-30
> **CatKiller said:**
> It just means that at some point your system needed to allocate 6.9 GB rather than the 6.8 you had available. Since your cruising level is 5 GB, that's not a lot extra; opening something in the Gimp, or a heavy browser tab, or whatever, can do that extra bit.

It's not something to worry about. Processes say "I need this much memory for this thing I'm doing" and the system says, "OK, then, here you go" and everything ticks along fine. A little bit now-and-then so that nothing ever has to not be able to allocate memory is what swap is *for*.

I'm using the default swappiness of 60 and with 16 GB of RAM my swap never gets touched for any of the things I normally do, since my computer is much better at multitasking than I am. Fire up Minecraft, though, and I'm *very* happy that there's an extra safety level for whatever horrific thing Java is doing with memory until it gets round to garbage collection.

As I'm sure you know, you don't want to get into the situation that you're *running things* from swap (which would mean that you need more RAM), but having that little bit extra available for housekeeping is perfectly fine.
So if I understand right, some data gets stored in the swap partition when the memory usage momentarily goes over 90%, and the data will stay there for the rest of the current session?

On a related point, I usually have Windows 10 running in VirtualBox. Maybe that is triggering the swap? I had a problem with system freezing on Manjaro KDE until I made a swap file. I couldn't see anything in System Monitor that indicated I was reaching my memory ceiling, but maybe it's that momentary thing you were talking about. 

I had a similar problem with Linux Mint 19 when I tried to run it on a laptop with 4 GB. I set the VM to 2 GB, and theoretically, there should have been enough memory to get by, but I had frequent system freezes. Mint 19 is supposed to install a swap file by default, if I understand right, but I still had freezes. 

Just trying to understand what's going on.

---

### Post by CatKiller on 2019-12-30
> **shmu26 said:**
> So if I understand right, some data gets stored in the swap partition when the memory usage momentarily goes over 90%, and the data will stay there for the rest of the current session?

Not necessarily the rest of the session, but till it's cleared by something. Cached files tend to hang around since they might turn out to be useful if you access the file again, and it's no slower to have the file remain in cache than not - writing to the memory address takes the same time regardless. An allocation for something like Java would get cleared on the next run of the garbage collector. Other applications free their memory whenever they free their memory.

Linux struggles hard in low memory situations and when it can't allocate requested memory it kills processes, more or less at random, until it can. Not a good place to be.

---

### Post by Yellow Pasque on 2019-12-30
> **shmu26 said:**
> I thought that swappiness set to 10 means swap will only be used when free RAM goes under 10%?

That's not what it means. Similarly, if you set swappiness to 0, swapping may still occur as long as swap is available (contrary to what a lot of people believe). The formula the kernel uses is:
```
swap tendency = mapped_ratio / 2 + distress + vm_swappiness
```
So vm_swappiness is used as part of the calculation, but it does not give you direct control over swap tendency.

[QUOTE=CatKiller]It just means that at some point your system needed to allocate 6.9 GB rather than the 6.8 you had available.[/QUOTE]

Not necessarily. The virtual memory manager is more proactive than that to prevent that situation.

---

