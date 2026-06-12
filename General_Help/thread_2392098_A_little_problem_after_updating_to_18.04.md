---
title: "A little problem after updating to 18.04"
date: 2018-05-16
forum: General Help
---

### Post by kpdenmark on 2018-05-16
Hello after I updated my system and installed all the same programs, I took a look at htop.
The VIRT is running crazy, normal those program is around 2 to 5 g.
Is that a bug or is that normal?

Acer aspire e 15
Intel i7-6500u
nvidia 950m
8 g ram
ssd 96 gb (running all on that)
1 tb hdd (storage drive uses for movies)

---

### Post by cruzer001 on 2018-05-16
I just did a fresh install of Mate one hour ago, this is what I get.
```
top -o VIRT
```
[ATTACH=CONFIG]279730[/ATTACH]

I don't think it matters.
> When is Virtual Memory Size Important?

The virtual memory map contains a lot of stuff. Some of it is read-only, some of it is shared, and some of it is allocated but never touched (eg, almost all of the 4Gb of heap in this example). But the operating system is smart enough to only load what it needs, so the virtual memory size is largely irrelevant.

Where virtual memory size is important is if you're running on a 32-bit operating system, where you can only allocate 2Gb (or, in some cases, 3Gb) of process address space. In that case you're dealing with a scarce resource, and might have to make tradeoffs, such as reducing your heap size in order to memory-map a large file or create lots of threads.

But, given that 64-bit machines are ubiquitous, I don't think it will be long before Virtual Memory Size is a completely irrelevant statistic.
[https://stackoverflow.com/questions/561245/virtual-memory-usage-from-java-under-linux-too-much-memory-used](https://stackoverflow.com/questions/561245/virtual-memory-usage-from-java-under-linux-too-much-memory-used)

---

