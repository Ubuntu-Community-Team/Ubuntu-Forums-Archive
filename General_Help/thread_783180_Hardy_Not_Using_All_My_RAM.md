---
title: "Hardy Not Using All My RAM?"
date: 2008-05-05
forum: General Help
---

### Post by cough on 2008-05-05
Hi All,

I have just installed Hardy Heron 8.04 Desktop (32 Bit) and have just noticed that ~ 13 - 15% of RAM is only being used - which seems like a very small amount to me. I recall in Gutsy and older versions of Ubuntu Linux that more than 90% of my RAM was being used...This is according to Gnome System Monitor.

I have 3gigs of RAM and it seems like a whole chunk of it is wasted. Is there anything I can do to better utilise it?

Thanks

Kahlil

---

### Post by pickboy87 on 2008-05-05
If you go under System -> Administration -> System Monitor and click on the System Tab...what does it say for how much ram you have?

---

### Post by FuturePilot on 2008-05-05
You have to watch out what you're looking at. There's a difference between used RAM and cached RAM. The 90% you saw probably wasn't used but cached. If Ubuntu was actually using 90% of your RAM I would have to say there's a problem. :lolflag:

```
free -m
```
will tell you. The line that says -/+ buffers/cache will tell you the actual used RAM.

---

### Post by cough on 2008-05-05
Thanks for the quick reply!

Here is the out put from: free -m

             total       used       free     shared    buffers     cached
   3043       2931        111          0         36       2467
-/+ buffers/cache:        427       2615
Swap:         3153         37       3115

Also, System Monitor says I have 3.0GiB.

Kahlil

---

### Post by pickboy87 on 2008-05-05
Your ram is showing up correctly as far as I can tell. You don't want your system to be using all your memory otherwise it would be slow.

Looks fine to me.

---

### Post by cough on 2008-05-05
Great, thank you. I was really unsure.

Kahlil

---

