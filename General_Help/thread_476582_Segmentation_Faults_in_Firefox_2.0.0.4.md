---
title: "Segmentation Faults in Firefox 2.0.0.4"
date: 2007-06-17
forum: General Help
---

### Post by DM was on fire! on 2007-06-17
I just recently upgraded from Ubuntu Dapper's default version of Firefox to the latest stable release, to hopefully get rid of the segfaults I've been getting. I followed the instructions in the Knowledge base, and I thought I was fine. Until about twenty minutes later, I got a crash while running it in terminal:

"/opt/firefox/run-mozilla.sh: line 131:  7739 Segmentation fault      "$prog" ${1+"$@"}

Whatever it is, it's obviously the same thing causing my [StepMania](http://www.stepmania.com/boards/viewtopic.php?p=28387) to crash, and most likely causing Ubuntu to log me out and freeze without warning.

Should I abandon Ubuntu? It obviously doesn't like me. XD

---

### Post by mikewhatever on 2007-06-17
Hi, I have no idea what segmentation is, but have you tried a different browser? Opera is the first one that comes to mind, and Konqueror and Galleon should be in the repositories, although they use Mozilla engine.

---

### Post by DM was on fire! on 2007-06-17
> **mikewhatever said:**
> Hi, I have no idea what segmentation is, but have you tried a different browser? Opera is the first one that comes to mind, and Konqueror and Galleon should be in the repositories, although they use Mozilla engine.

Segmentation is memory management and/or protection.
[http://en.wikipedia.org/wiki/Segmentation_%28memory%29](http://en.wikipedia.org/wiki/Segmentation_%28memory%29)
[http://en.wikipedia.org/wiki/Memory_management](http://en.wikipedia.org/wiki/Memory_management)

I installed Opera and Epiphany, and both crash on me as well.
I'll try Konqueror. I didn't know if I had it on here or not.

---

### Post by Lanky Juggler on 2007-06-17
I think I've been getting the same problem for ages, ever since I upgraded to feisty (fresh install, too).  For me, though, it only has the segmentation fault when I don't clear my private data and the autocomplete has more than about 10 items in it.

---

