---
title: "turning off memory cache"
date: 2007-01-16
forum: General Help
---

### Post by maniacmusician on 2007-01-16
Is there any way to turn of the caching of RAM to increase performance on things like virtual machines? 

also, my current motherboard/processor doesn't handle caching very well so I thought I would try living with it turned off for a couple of days.

So basically; how do I disable the memory cache function?

Thanks

---

### Post by defishguy on 2007-01-16
Are you talking about the swap partition?  Caching is a very good thing for the most part.

---

### Post by maniacmusician on 2007-01-16
nope I mean caching.

When I'm running a virtual machine, I give it an alloted amount of ram, say 512; but I don't want it to be using 512 the whole time as that affects the performance of the host system. I want it to use the bare minimum. To do this, I have to somehow disable memory caching.

---

### Post by dcstar on 2007-01-16
> **maniacmusician said:**
> nope I mean caching.

When I'm running a virtual machine, I give it an alloted amount of ram, say 512; but I don't want it to be using 512 the whole time as that affects the performance of the host system. I want it to use the bare minimum. To do this, I have to somehow disable memory caching.

Possibly there are some kernel boot options for this, otherwise it may be a kernel compilation option that you can select.

---

### Post by mdurham on 2007-01-16
> When I'm running a virtual machine, I give it an alloted amount of ram, say 512;
Why can't you give it less?

---

### Post by maniacmusician on 2007-01-17
I suppose I could give it less, I'm just messing about though. It's a bummer that there's no easy way to do it.

---

