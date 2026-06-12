---
title: "Memory/RAM Disk Caching"
date: 2014-12-01
forum: General Help
---

### Post by box02-0 on 2014-12-01
Hi. 

I am installing Ubuntu 14.04 on my new computer which has twin Samsung Pro 850 ssd's, and 32gb RAM. (Mostly only one ssd will be in use at any one time.)

Samsung uses a Windows program called Magician, which allows for the allocation of so many gigs of RAM to be used as Disk Caching (RAPID).

(I will not be allocating a Swap Partition on the ssd's.)

Questions:
1. How does Ubuntu handle Disk Caching? Can it handle multiple physical disks?

2. What is the difference between Memory Cache and Disk Cache? (I read somewhere that they can not run simultaneosuly.)

3. Is Memory Caching or Disk Caching enabled by default?

4. Should I be using the 'Preload Adaptive Readahead Daemon', and how does it interact with the Memory or Disk cache? How is it enabled?

5. What is a good Monitor Program to display useage of Disk or Memory Cache?

Thanks,

M....

---

### Post by grahammechanical on 2014-12-01
I have installed System Load Indicator. It is in the Software Centre. I find it useful for monitoring certain aspects of hardware. Right now System Load Indicator is telling me that out of my 1GB RAM, 695MB is used and 247 MB is cached. I have done nothing to enable caching. It is taken care of automatically by the Linux kernel.

Accurate information about technical terms is much better than opinion.

[http://en.wikipedia.org/wiki/Disk_cache](http://en.wikipedia.org/wiki/Disk_cache)

[http://en.wikipedia.org/wiki/Page_cache](http://en.wikipedia.org/wiki/Page_cache)

[http://en.wikipedia.org/wiki/Page_cache](http://en.wikipedia.org/wiki/Page_cache)

> [COLOR=#252525][FONT=sans-serif]While CPU caches are generally managed entirely by hardware, a variety of software manages other caches. The [page cache]("http://en.wikipedia.org/wiki/Page_cache") in [main memory]("http://en.wikipedia.org/wiki/Main_memory"), which is an example of disk cache, is managed by the operating system [kernel]("http://en.wikipedia.org/wiki/Kernel_(computing)").[/FONT][/COLOR][COLOR=#252525][FONT=sans-serif]

With 32GB of RAM it is most unlikely that Windows will use its swap file or that Ubuntu will use its swap partition. 

> Paging is an important part of [virtual memory]("http://en.wikipedia.org/wiki/Virtual_memory") implementation in most contemporary general-purpose operating systems, allowing them to use secondary[SUP][[a]]("http://en.wikipedia.org/wiki/Paging#cite_note-3")[/SUP]storage for data that does not fit into physical [random-access memory]("http://en.wikipedia.org/wiki/Random-access_memory") (RAM).

[http://en.wikipedia.org/wiki/Paging](http://en.wikipedia.org/wiki/Paging)
[/FONT][/COLOR]

Caching data in RAM is not the same as caching data on a hard disk, although it seems that both can be called "disk cache."

[http://askubuntu.com/questions/110335/drawbacks-of-using-preload-why-isnt-it-included-by-default](http://askubuntu.com/questions/110335/drawbacks-of-using-preload-why-isnt-it-included-by-default)

Regards.

---

### Post by box02-0 on 2014-12-03
Hi and thanks for your informative reply. I think I got it now. 

Just a question on: Should I be using the 'Preload Adaptive Readahead Daemon'?


Thanks,

M...

---

### Post by mcduck on 2014-12-03
Depends on what you want. It can make the preloaded applications start quicker, but at the expense of slower system boot and higher memory usage.

So it really depends on how you use your computer, in some cases it can speed things, in others it can make things slower. The first answer here explains it pretty well: [http://askubuntu.com/questions/110335/drawbacks-of-using-preload-why-isnt-it-included-by-default]("http://askubuntu.com/questions/110335/drawbacks-of-using-preload-why-isnt-it-included-by-default")

---

### Post by ibjsb4 on 2014-12-04
Thats a nice link mcduck.

This install has been running for three weeks with preload installed; output of free -m.
> Mem: used-18932M; free-5173
-/+ buffers/cache:       1760;      22344

So I rebooted it.
> Mem: used-1005M; free-23099
-/+ buffers/cache:        461;      23643

Then I removed preload.
> Mem: used-602M; free-23657
-/+ buffers/cache:        447;      23657

Preload seems to be behaving its self, but I can't say that its doing anything great either.  Linux cache does a good job by its self.  May be a better app for older machines.  I have preload installed on my older dual core laptop and I think it helps there.

---

