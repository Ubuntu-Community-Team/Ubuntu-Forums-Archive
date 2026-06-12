---
title: "article (slow linux and how to fix it) - swap"
date: 2007-10-04
forum: General Help
---

### Post by bone2006 on 2007-10-04
I was reading this article:

[http://tinyurl.com/369mwp](http://tinyurl.com/369mwp)

and notice that it explains how the swap slows down the system and things to do.  Would it essentially have the same benefits if I used gparted and removed the swap partition?

---

### Post by elliotjreed on 2007-10-04
I would not remove the swap. Basically what it does, is if your memory gets too full, it starts offloading it into the swap - like in windows when it starts using 'virtual memory'.

Removing it will not be to your advantage, as it only does this when very necessary!

---

### Post by bone2006 on 2007-10-04
that is what I thought, but the article made it seem as if for desktop users who use multiple applications that it's not a good idea, because the swap is slower.  I've seen many linux user who no longer use swap

---

### Post by bone2006 on 2007-10-11
maybe this is something I don't understand then. After reading the article I'm almost lead to believe that removing my swap partition would be better.

When I type free in the command I see that there's swap being used, even though I'm not even close to running out of RAM

r:~$ free
                   total       used       free     shared    buffers     cached
Mem:        254776     249900       4876          0        848      36820
-/+ buffers/cache:     212232      42544
Swap:       546168      50536     495632

Not sure why Swap is being accessed, especially since I'm to believe it's slower than RAM

---

### Post by Sef on 2007-10-11
How much ram do you have?

---

### Post by bone2006 on 2007-10-11
The command I post I believe tells you 256mb.  This is just one of my systems though.

I have a 1GB ubuntu 64bit system and I really really noticed copying a 700mb file puts my computer at a halt until it's done copying.  I really can't multitask and the article explains it.  Kind of confusing though on what to do compared to removing swap completely.  Seems that maybe this wouldn't happen if I didn't have a swap partition?

---

