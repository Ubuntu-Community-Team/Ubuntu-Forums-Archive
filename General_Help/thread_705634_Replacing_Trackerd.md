---
title: "Replacing Trackerd"
date: 2008-02-23
forum: General Help
---

### Post by banelos on 2008-02-23
First of all thanks to all the people willing to answer the endless amount of questions from us linux newbs, we owe you.

My problem is with the file searcher/indexer Trackerd.. I have switched indexing off since I've always been against wasting resources on that, but now it seems trackerd doesn't return any results no matter what I search on.

Is this just because i turned indexing off or? It won't find any results in the search deskbar applet or if I search from inside the file manager.. So if I can't get it fixed, I'd rather just switch to another file searcher.. But which file searchers do you recommend and do they integrate with the file manager as well as Trackerd? I'm not even sure if it is Trackerd that does the file searching from within the file manager really, so correct me if I'm wrong.

Thanks in advance to anyone who can help me.

---

### Post by ajgreeny on 2008-02-23
You could try beagle, which was the file searcher used in previous versions of ubuntu.  I do think the reason you get no results is that you have turned off trackerd, and if you want results you should turn it on again.

I suggest you try to reindex again at a time when the computer is not being used.  It can take some time and once done should give you a better search of files, and the system should not be using too much of your cpu or other resources.  Most of the time I find trackerd is sleeping if I look in system monitor, and not taking up any resources at all.  I don't know if that is normal or if I'm just lucky, but I would find it less than my needs to have the file search unavailable; it's so useful to me.

Use terminal and do the following ```
killall trackerd
trackerd -v 2 -R
```That should do the trick.

---

### Post by banelos on 2008-02-23
Ok that did the trick, thanks a ton aj.
I was just of the understanding that I could still force it to manually search for files from within the file manager even if I weren't indexing.. A bit like how windows search works I guess. But after doing the full reindexing as you suggested it works perfectly.

---

