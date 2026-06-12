---
title: "Can you cut parts of the kernel out you dont need?"
date: 2019-03-24
forum: General Help
---

### Post by iamtheeggman2 on 2019-03-24
In order to make the pc faster?

Just curious

---

### Post by TheFu on 2019-03-24
> **iamtheeggman2 said:**
> In order to make the pc faster?

Just curious

You have access to the source code and are free to modify it anyway you like for any purpose within the GPLv2 license restrictions.  Whether any changes make it faster or not is completely up to you.  Whether any of those changes introduce huge security gaps is also up to you.

Tuning a kernel for performance based solely on existing compile options is usually not fruitful by normal people.  I attempted to do it in the 1990s, before kernel drivers were loaded through modules.  I did make the code loaded smaller, but my attempts made it measurably slower when compared to the kernels produced by Redhat.

As with any software, the only way to determine where all the time should be spent on code optimizations should come from facts gathered through profiling specific use-cases. Then there is hope.  Doing this is non-trivial.

A kernel with less code doesn't directly lead to a faster kernel.  IMHO, the best way, cheapest way, easiest way, to make a system faster is by getting new hardware.  For a $300 upgrade, almost any 3 yr old system can be 2x faster.  Whereas hiring an expert to tune your kernel would need at least 5 hrs - at $150/hr and might get a 5% improvement, maybe.

---

### Post by iamtheeggman2 on 2019-03-24
heh, i thought id see what my graphics card could do by downloading a linux game alien arena however it doesn't play with sound and i am not of the mindset to muck about for hours trying to work out why not either. gonna uninstall it me thinks.

i dont know why but lubuntu has been feeling sluggish, i guess that's because over time they add more and more code? i was pleasently surprised to see how fast windows 8.1 run on my dell lalttidue d630

---

### Post by wildmanne39 on 2019-03-24
Hello iamtheeggman2, please stay on topic, we allow one topic per thread, the reason is when searchers find a solved thread it will actually be about the topic in the title, plus all support sub-forums are strictly for support so searchers do not have to look through 100 posts to find the answer because of chit chat, discussions have there own sub-forum.

Thanks

---

### Post by VMC on 2019-03-24
I can't find the older artical regarding linux shell. But it stated something along the lines that the user has access to the outer shell and not the inner where the "speed" of the kernel takes place.
Here's one answer:
[https://askubuntu.com/questions/99759/does-compiling-a-linux-kernel-make-the-os-faster](https://askubuntu.com/questions/99759/does-compiling-a-linux-kernel-make-the-os-faster)

There are a few places that effect performance, services, mods, etc. See this map of the user space that you can change. I slimmed down my kernel years ago with the same idea of speeding up the process. Nothing changed.
[http://www.makelinux.net/kernel_map/](http://www.makelinux.net/kernel_map/) 

You would need a lot of knowledge of the kernel to make an effective change.

---

### Post by TheFu on 2019-03-24
> **iamtheeggman2 said:**
> i dont know why but lubuntu has been feeling sluggish, i guess that's because over time they add more and more code? i was pleasently surprised to see how fast windows 8.1 run on my dell lalttidue d630

If lubuntu feels sluggish, I'd look for driver selection problems (especially the GPU) and hardware faults. Faults should show up in the system log files.  At some point, SATA cables start going bad. Things work, but have to be re-transmitted due to corrections.  Same for disk storage as a drive gets older, sometimes it needs to relocate data from bad sectors. The more of those there are, the slower the system will become.  Check the system logs.

Well maintained Linux systems don't slow down over time, unlike Windows.

---

