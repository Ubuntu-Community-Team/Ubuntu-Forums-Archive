---
title: "[SOLVED] RAM problem"
date: 2008-04-26
forum: General Help
---

### Post by Stefanie on 2008-04-26
Just after startup, free -m says i'm using 560 MB RAM. The system monitor, however, says i'm only using 296 MB. Which is the correct number? If 560 is correct, why is it so high?

---

### Post by bingoUV on 2008-04-26
> **Stefanie said:**
> Just after startup, free -m says i'm using 560 MB RAM. The system monitor, however, says i'm only using 296 MB. Which is the correct number? If 560 is correct, why is it so high?

Both are correct. Both define memory usage differently so they manage to be different and correct at the same time. 
 
 There are many kinds of memory usage. Since this is a question on linux internals, it cannot be explained via fairy tales, be prepared to read a bit involved explanation. Have patience, it will not seem complicated once you understand it. This is one of the simplest explanations I could find.  
 
Read [http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419).

---

### Post by Stefanie on 2008-04-26
Thank you very much. Right now i'm using 807 MB out of 1003 MB according to free -m (cached 349) and 437 MB according to the system monitor. 
So the difference between them is due to the cached memory? If I understood it correctly, the 349 cached MB is in fact spare MB that is cached to improve performance. So this means that I'm not running short on RAM at all?

---

### Post by Linja on 2008-04-26
Don't worry, the moment you run out of memory, you'll notice. The kernel will start swapping out memory pages and performance will drop to maybe 10% of what you are used to. That won't happy any time soon with 1GB, though.

---

