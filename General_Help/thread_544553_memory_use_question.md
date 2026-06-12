---
title: "memory use question"
date: 2007-09-06
forum: General Help
---

### Post by electronpusher on 2007-09-06
Actually I'm not even having a problem- my computer is working fine- so far.I'm using Ubuntu Dapper on several old computers with only 256mb. of RAM. When I boot up I noticed that the amount of RAM that GKRELLM reports varies considerably. This is with NO change to the computer configuration. I have gotten figures as low as 190 mb and at times as high as 206 mb. I am using the ICE window manager. Why does this happen? Since I run GKRELLM immeadiately after booting shouldn't it always give the same figure? Another curious thing: If for instance I start Thunar and check memory consumption with Gnome System Monitor it might say that Thunar was using something like 10 mb- but if I look at GKRELLM the amount of RAM reported does NOT go down by 10 mb! Maybe only half that! I think there is a lot I don't understand here. Are there any good books about Linux memory usage and how it works? I couldn't have a virus could I?
   Thanks to everyone for any help on satisfying my curiosity!

---

### Post by jnorthr on 2007-09-06
Virus is unlikely. This senario sounds normal to me. The variations are naturally occuring due to several factors, such as swap space usage, the normal startup processes which examine your peripherals, say for example the disks. Some disk may need extra checking if it has not closed down successfully before, or the structure of the files and their directories have not been checked lately (this is done periodically). If you have wireless activity or not on your system; log files may overflow and require further attention; spool file cleanups may happen in the background; there are a whole host of reasons why you would see a difference. I would think it quite unusual to see the same memory patterns more than once or twice. For further research go here: [http://safari.oreilly.com/search](http://safari.oreilly.com/search) and in the advance tab on the left try 'linux memory management'. There are several good books to give you a more firm understanding of these processes. It's a fascinating subject that's occupied the great minds since the dawn of the modern computer in Bletchley Park during WWII.

---

### Post by pmg on 2007-09-06
> Another curious thing: If for instance I start Thunar and check memory consumption with Gnome System Monitor it might say that Thunar was using something like 10 mb- but if I look at GKRELLM the amount of RAM reported does NOT go down by 10 mb! Maybe only half that!
This could be explained by the tool using shared libraries.  This program is using them, and so they are counted as part if it's memory usage, but they are only loaded into memory once for the whole system and all running programs needing them use that same one copy, rather then each program loading it's own copy in memory.

---

### Post by fragos on 2007-09-07
Check out the "free" command.  It tells you how memory, real and swap, is being used.  Some boot procedures run in parallel and finish in different orders on the same machine.  This can result in memory use looking different.  I used the "free" command to help determine if my memory configuration gave optimum perform by not using swap space.  With my usage patterns, 1GB is enough to rarely use swap space.  With 256MB, more memory would be a simple low cost performance enhancer.

---

