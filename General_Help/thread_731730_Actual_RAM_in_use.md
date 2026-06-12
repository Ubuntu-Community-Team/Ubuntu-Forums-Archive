---
title: "Actual RAM in use?"
date: 2008-03-22
forum: General Help
---

### Post by nisarg on 2008-03-22
I run a applet on my panel to monitor CPU, Memory, SWAP and Disk in order as shown in the screenshot.
Am I correct in thinking I need more RAM? I seem to have hit 100%. 
But a large portion of it is in "use by Cache". the blue-portion in the Memory monitor. The green-portion is memory in 'use by programs'. From the screenshot it seems I have approximately 45% (programs) - 55% (cache) ratio.  
Can someone throw some light please - what excatly does 'in use by programs' and in 'use by cache' mean?
Cheers.

EDIT: for information i ain't running compiz or anything fancy like that at time when I took this snapshot.

---

### Post by fela on 2008-03-22
don't worry, ubuntu can live with 256MB RAM as long as you don't do loads of stuff at once. How much RAM do you have? Cause i hav 1.1gb and it's always telling me like 100% is used including cache, my system runs fine though. I think you should think about upgrading only if you notice performance drops, or if your a RAM addict :lolflag:.

---

### Post by hyperair on 2008-03-22
It will always be at 100%, with the space not occupied by your programs used for cache instead, as it'll help for faster loading that way. Don't bother about the cache memory, just care about your program used memory, as well as your swap. If I'm not mistaken I think not all the memory you have will be used for programs. There will always be some reserved space. Instead, the swap will be filled. So, if your swap reaches 75% or more then increasing your RAM will definitely give you better performance.

---

### Post by schiznik on 2008-03-22
There are a billion and one articles across the web on this issue, so I wont go into too much detail.. however I will say that "unused RAM is wasted RAM".

"In use by programs" is effectively the equivalent RAM usage that windows shows.
"In use by cache" is data that instead of being written to the much slower swap space, is being held in the RAM itself for fast access should it be needed. If a program needs this cached RAM, it will be freed so that the program can use it. 

Basically, if you are using alot of swap continually, you need more RAM. If you are never using any swap, then linux is using all of your RAM as efficiently as it can, by caching as much as possible that would otherwise be written to disk in the swap space.

---

### Post by nisarg on 2008-03-22
Thanks.

I guess - it might be too hasty to get some more RAM now while I am not going to see a performance gain anyways I guess? Will I ?

---

### Post by schiznik on 2008-03-22
You might see a little, have a look when your pushing your computer rather than when its mostly idle. If you end up with virtually all your ram used by programs and minimal cached, and alot of swap, then get some more, its cheap these days...

Otherwise, it seems fine to me

---

