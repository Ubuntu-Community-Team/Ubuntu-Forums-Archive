---
title: "Excessive RAM Usage During Operations"
date: 2008-06-17
forum: General Help
---

### Post by Exsecrabilus on 2008-06-17
One time, I was copying the files from a DVD (I copied movies to it before I was fresh-installing Hardy so I wouldn't lose my videos.)
After five seconds, my computer went into a frenzy and became unresponsive. It took like one minute to move the cursor like 20 pixels.
I guessed something was wrong, but let it go.

Today, I saw security updates available in *Update Manager*, so naturally, I opened it up and clicked *Install Updates*.
Suddenly, my computer became slow and unresponsive again, just like when I was copying files from the DVD a few days back.
Remembering what happened before, I quickly opened up System Monitor to see what was wrong.
And guess what? **97% OF THE RAM WAS BEING USED. ALL BY UPDATE MANAGER.** I had nothing else open, and I have 1 GB of RAM.

Is there any solution to this excessive RAM usage issue?

---

### Post by rsaavedra on 2008-06-17
Don't know how to get around that problem, but I recently submitted [this post]("http://ubuntuforums.org/showthread.php?t=832559&referrerid=581726"), where I report observing Ubuntu go extremely slow, but in fact at just 80% of RAM utilization.  It was a laptop with just 256 of RAM though, so my case is rather different, but odd thing is, according to the System Monitor Ubuntu wasn't using the swap file at all.  Makes me wonder if there's some bug in the memory management logic of Ubuntu.

---

