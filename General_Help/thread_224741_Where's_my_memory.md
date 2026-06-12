---
title: "Where's my memory??"
date: 2006-07-28
forum: General Help
---

### Post by AlliumPorrum on 2006-07-28
I have Ubuntu running on a laptop with 384MB of RAM. I checked with 'free -m' what might be the situation with the free memory, and it shows like this:

jasurakk@jasurakk-dell:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           376        367          8          0         72        205
-/+ buffers/cache:         89        286
Swap:          501          0        501

So if I understood correctly I'm soon running out of memory, because there is only 8MB's of "real" memory left. I started wondering that how it is possible because there really aren't so much applications running on my computer; just MySQL and 2 my own Java applications, they take something like 70MB's in common. So I runned 'ps aux' to see who is reserving all that memory, output of that is in attached file. If you count memory of all processes (isn't it that RSS column??) together, it makes 108,9MB's.

So my question is; how is it possible that 'ps aux' shows that processes use 108,9MB's of memory in common, but 'free -m' shows that amount of used memory is 367MB's?? Where is that 260MB's lost??

---

### Post by DoktorSeven on 2006-07-28
See the values under buffers/cache?  That's your actual free memory.  Linux uses buffers and cache to load things faster, but it's actually free memory.

So, in short, you have 286M of memory free.

---

### Post by testube_babies on 2006-07-29
If you want to see where your memory is devoted at any given time, open a terminal and type "top"

I find that generally all of my memory is used up, but my swap space is mostly free.

---

