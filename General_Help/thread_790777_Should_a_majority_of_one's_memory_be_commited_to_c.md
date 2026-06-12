---
title: "Should a majority of one's memory be commited to cache?"
date: 2008-05-11
forum: General Help
---

### Post by Lord Xeb on 2008-05-11
When I am running Ubuntu, after a while (maybe and couple of hours) 60% of my memory is devoted to cache. Right now it is 15% used and 15% cached. After about an hour running firefox it will be nearly 60% cache. Is that normal?

---

### Post by chewearn on 2008-05-12
Yes, it's normal.  This might sounds counter intuitive, but here goes:

[I]Unused (or free) memory is wasted memory.
[/I]Think about it.

.

---

### Post by sdennie on 2008-05-12
As AstalaVista said, it's a good thing.  It has no adverse effects on your system and, in fact, generally makes your machine more responsive (especially when frequently opening/closing apps).  When your applications need more memory, linux will just start dumping parts of the cache so your apps can use that memory but after using your system for a while, you are likely to have almost no RAM "free".  If you subtract the amount of RAM devoted to cache, that's the actual amount of free RAM.  The command:

```

free -m

```

Shows this pretty nicely.

---

### Post by kevdog on 2008-05-12
Here is an interesting link on the same subject:

[http://ubuntuforums.org/showpost.php?p=4088251&postcount=150](http://ubuntuforums.org/showpost.php?p=4088251&postcount=150)

---

### Post by Lord Xeb on 2008-05-12
O_O ******* AWESOME!!! >_> -1 for M$ and another +1 for Linux *is filled with excitement and runs of the go tinker with machine*

---

