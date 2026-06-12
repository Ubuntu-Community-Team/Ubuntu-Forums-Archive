---
title: "[ubuntu] How Do You Clear RAM and Allocate More to an Application?"
date: 2015-07-27
forum: General Help
---

### Post by Bubblegut on 2015-07-27
Hi, I am trying to run Minecraft on my 12.04 Ubuntu 2gb memory system and am having issues with RAM. This is a two-part problem.

1. In-game, memory comes up as 499 with 100% allocated. I'm wondering how to allocate more ram (at least 1gb) to the game. I have tried:
```
java -Xmx1024M -Xms1024M -jar /home/id/Desktop/Minecraft.jar
```
but there seems to be no difference on re-boot. Is this the right method?

2. My memory actually appears to be full, with only 11% remaining. Using ```
free -m
``` returns:
```
total       used       free     shared    buffers     cached
Mem:          2013       1881        131          0          1         93
-/+ buffers/cache:       1786        226
Swap:         5894       1847       4047
```
I am only running the game and Google Chrome at this time. What could be eating my memory? I do not believe this is a case of disk caching. What do I need to do to clear my RAM?

Thanks in advance for any help.

I managed to allocate more memory to the game, 1GB (says  921 in-game). It still fills up the RAM just as quickly though, so I am wondering if I allowed it to use memory that isn't even there. Any ideas for clearing RAM?

---

### Post by Bubblegut on 2015-07-28
Bump.
200 views but noone has any input? Ahuh...

---

### Post by howefield on 2015-07-28
You posted less than a day ago, be patient and continue to bump (once per day or so) if need be.

Incidentally, apart from you and me, there are only 4 of the 200 views that are forum members, the rest are search engine spiders, guests and the like, none of whom can reply to your post.

---

