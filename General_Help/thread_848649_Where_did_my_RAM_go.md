---
title: "Where did my RAM go??"
date: 2008-07-03
forum: General Help
---

### Post by donnyblaze1 on 2008-07-03
I installed Xubuntu Hardy about 2 weeks ago.  Since then, my machine has consistently shown between 1200mb - 1300mb RAM free.  Now today when I turn the computer on, it says I have 461mb free.  What happened?  I have not installed anything new or changed any configuration since last night...when it showed over 1200mb free.  The memory is all being recognized...htop just tells me its all being used...however no process in htop shows up as using more than 3% of memory.  Where is all of this RAM going???

---

### Post by sdennie on 2008-07-03
Try using "free -m".  The output should look like this:

```

             total       used       free     shared    buffers     cached
Mem:          4049       2451       1598          0        482       1244
[COLOR="Red"]-/+ buffers/cache:        724       3325
[/COLOR]Swap:         4000          0       4000

```


The red line is the interesting one.  My guess is that most of your RAM is being used by the cache which is normal and not what most people would consider to be "used" RAM.

---

