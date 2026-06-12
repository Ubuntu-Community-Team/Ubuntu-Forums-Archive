---
title: "Alot of memory just running X"
date: 2007-06-04
forum: General Help
---

### Post by Kuraudo on 2007-06-04
Hello,

When I run no program på htop in a terminal window I use 218MB of my memory. I think that's very much for just running X.

Anyone knows why that could be?

I have 1024MB of memory.

---

### Post by kidders on 2007-06-05
Hi there,

Are you sure all 218MB are actually in use (ie rather than just "not free")?

> **Kuraudo said:**
> Hello,

When I run no program på htop in a terminal window I use 218MB of my memory. I think that's very much for just running X.

Anyone knows why that could be?

I have 1024MB of memory.

---

### Post by Kuraudo on 2007-06-06
> **kidders said:**
> Hi there,

Are you sure all 218MB are actually in use (ie rather than just "not free")?

How can I tell if the memory is in use or just "not free"?

---

### Post by mcduck on 2007-06-06
> **Kuraudo said:**
> How can I tell if the memory is in use or just "not free"?

Run 'free -m' in a terminal, and then take a look at the '-/+ buffers & cache'-line. It tells you the actual memory used and available for programs. (Linux uses all RAM not used by programs as disk cache. This makes file access faster in many cases, and anyway memory not used is memory wasted ;)).

---

### Post by kidders on 2007-06-06
Linux comes with a few basic memory usage analysis tools (eg top, free, vmstat, etc). Their man pages are a good place to look for information on how to interpret what they tell you. You might also find it helpful to read a little about Linux's memory management model.

In general terms though, Linux's apparent _system-wide_ memory usage should be quite high, since it is (by default) reluctant to waste time performing pointless deallocations, and likes to use large chunks of RAM for buffer space, when it's not in use for other things. That's why, in my last post, I asked whether you were sure what the figure you mentioned really was. At the moment, for instance, my Xorg is using about 63 MiB of RAM, after having used it for several hours. I have 9 free megabytes, but that doesn't mean that more RAM can't be reclaimed, if I suddenly do something that needs 500.

I hope that helps a little.

[[SIZE=1][COLOR=Silver]UAResolved[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by Kuraudo on 2007-06-10
Perfect :)

No I don't really know much about how Linux uses RAM but I'll read about it.

But thanks for the answers. I thought that I didn't have any RAM "left" and therefor it would be very troublesome to run any more programs. But that wasn't the case, thank god :)

Edit: I ran free -m and I had 9 MB that wasn't used of my RAM, which feels right. But 500 of that was "cached". But if I got it right Linux will cache the things in my memory to my swap that I don't need right now if I will run something else that needs more RAM. Or?

---

### Post by kidders on 2007-06-10
Hey again,

That's more or less accurate. :-) Essentially, the idea is that Linux will (by default) try to use as much of the resources available to it as possible. As a result, you will notice things like processes that appear to use far more of the CPU than seems reasonable, or vast chunks of RAM being "wasted" on caching, in an effort to boost performance.

Another typical quirk that you might notice is that when you type "top", and take a look at how much *virtual* memory is in use, what you'll most often be seeing is effectively the maximum amount of swap Ubuntu has needed at any one time, since you last rebooted (rather than the amount in use right at that moment). This is because virtual memory is not always deallocated right away.

The downside to all this is that resources that are neither "in use" nor "free" can't always be reallocated quite as quickly as would be nice, but that only becomes an issue on certain specialised systems that don't make the overall gain the scheme is designed to give you.

Anyhow, chances are your system is working the way it's supposed to. :-)

---

