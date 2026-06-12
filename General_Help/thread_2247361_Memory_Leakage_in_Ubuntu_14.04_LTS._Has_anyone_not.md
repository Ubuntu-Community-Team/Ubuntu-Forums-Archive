---
title: "Memory Leakage in Ubuntu 14.04 LTS. Has anyone noticed it?"
date: 2014-10-07
forum: General Help
---

### Post by rui-sarmento on 2014-10-07
[COLOR=#000000][FONT=Arial]I've been working with the mentioned Desktop OS and been having problems with memory leakage. I'm yet to be able to detect responsible process. Is it something anyone has noticed also?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm using this desktop to run LAMP Server and after some hours my 32GB just disappears into 200MB of free memory...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I've used top command to detect what eats all memory without success. I've also listed top-10 processes ordered by used memory and it is all ok. No process listed makes understandable why the memory is being used this way.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Any help will be appreciated.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]All the best![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]EDIT: - To add to the confusion please see attached figure with top and system resource display:

[IMG]http://i.stack.imgur.com/Ql4zI.png[/IMG]


[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-10-07
This is what I have found out and I may be inaccurate. System Monitor does not include cache memory in its total of memory used. Top does seem to include cache or buffer memory in its total of memory used. So, we are not comparing like with like.

I have also noticed that 14.04 or the LInux kernel is making better use of cache memory. The OS will claim a certain amount of RAM as a cache and as memory needs increase it is memory from cache that is used rather then claiming more RAM.

I have also noticed that 14.04 is quicker at freeing up RAM. In the past once RAM was claimed for a process it was often held as used memory for a time in case that process required it again. And so free memory got less and less. But this is not happening in 14.04. In fact if I leave the OS idle and then start closing applications, memory is freed so quickly that opened apps are so slow to respond to user actions for a few seconds. Memory used can drop to less than 30% of my 1GB of RAM when it is about 50% at start up.

Is this affecting performance? System resources are there to be used. I find System Load Indicator to be useful for monitoring resource usage.

Regards.

---

### Post by irv on 2014-10-07
Just a quick note: When I setup my server (14.04) this pasted month, I saw memory leakage error and after checking it out found there was a bug in Samba that was causing it. I believe they were working on it and might even have it fixed now. I uninstalled it and had to make a few other changes to get rid of it so I am not using it right now.

---

### Post by mcduck on 2014-10-07
Actually you have ~12GB of free RAM. 

23026B (free) + 174120 (buffers) + 12181000B (cache) = 12378146B = 11,8GiB
(Linux will always use any otherwise unused RAM as cache for recently used files. As cached data can be dropped immediately if any process needs more memory, it counts as "free" from any program's perspective. So that aposrt of the memor is used to speed up your system, but is still available for processes as soon as they ned it. Buffers work more or less the same way, in the sense that they can be flushed quickly if the memory they are suing is needed for something else. So if youa re just lookign at the "free" value in top, it should always approach to 0 once the system has been running for a reasonable amount of time. That's not a memory leak, it's the system usign all the available memory for best performance, empty memory doesn't help anything and as long as it's available for apps when they need it, using it for something else makes perfect sense. This  is also why the System Monitor counts "free" to include the RAM used as cache.) 

That being said, the 19GiB you are using is of course quite a lot. Try sorting the processes based on resident memory use (RES) in top for a better idea about where it's used.

---

### Post by jaydlowrider on 2015-02-27
> **irv said:**
> Just a quick note: When I setup my server (14.04) this pasted month, I saw memory leakage error and after checking it out found there was a bug in Samba that was causing it. I believe they were working on it and might even have it fixed now. I uninstalled it and had to make a few other changes to get rid of it so I am not using it right now.


I think this is accurate, I also have noticed the problem when I attach to my NAS backup server and actually do my backup. 

Melvin

---

