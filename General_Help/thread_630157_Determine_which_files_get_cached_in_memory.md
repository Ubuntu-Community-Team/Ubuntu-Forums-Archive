---
title: "Determine which files get cached in memory"
date: 2007-12-03
forum: General Help
---

### Post by Milk &amp; Toast &amp; Honey on 2007-12-03
Hi, 

I have a few questions regarding file system cache, specifically the read cache. I found similar thread in this forums, but the threads doesn't seem to answer my specific question.

I believe Linux cached *all* the files readed to the memory. This includes small and big size files from anywhere in the filesystem.

My questions are:
[LIST=1]
[*]Is there anyway to make Linux to cached only specific part of the *filesytem* and to ignore the others?
[*]Or can we tell Linux to *hold* the specific cache for certain part of *filesystem* that won't get "flushed" (cleared from cache) when the system need to cache another "unimportant" file? Basically, this one is like a "cache priority", where one cached file won't get replaced by the other file that has a lower "cache priority".
[/LIST]

I have this thought because I do believe if we can determine which parts of *filesystem* have more priority to stay on the cache, we can *improve* system responsiveness, e.g: the "program cache" won't get flushed if the users is copying some large files, which will cut the read time if later, the user open the very same program. We can also apply this to the library (*.so) files. Please tell me if I'm wrong in this specific case.

I have googling and goofing around but found nothing that even close to my question, this maybe because I don't know what is the exact term to search regarding this question.

I really appreciate if you have any idea and wants to lighten me.

Thank you very much.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-12-04
Hi, anyone have any idea yet?

---

### Post by bingoUV on 2007-12-04
For a simple solution, read second part of the page [http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/2/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/2/)

which is titled "Filesystem caches are more important than other caches".  It sets parameters in the kernel to prioritize different types of cache. It also gives a very simple test script which can tell you how much improvement has been achieved.

To customize your system according to your requirements, and to understand fully the tweaks recommended above, you might need documentation of /proc filesystem. Read [http://www.linuxinsight.com/proc_filesystem.html](http://www.linuxinsight.com/proc_filesystem.html) for starters.

If nothing else, the above links will give you enough terms to google around.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-12-04
bingoUV, thank you for your reply, but I had already red both links you gave (before I make this thread :) ), and it doesn't solve my questions. Previously, I also have read the vm/*, filesystems/proc.txt in kernel source's documentations, but I can't find the answer or the way to accomplish my question there.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-12-05
Sorry, but... *up up up*

---

