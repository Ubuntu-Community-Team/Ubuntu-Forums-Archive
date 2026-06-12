---
title: "how to itemize ram usage?"
date: 2008-05-04
forum: General Help
---

### Post by kabanta on 2008-05-04
I am trying to figure out the *details* of RAM usage for a Hardy server installation. The solution needs to be *terminal based*, rather than, say, the gui-based "System Monitor."

If I run **top**, something like the following is *summarized*:

[INDENT]Mem:   1026136k total,   *812024k used*,   214112k free[/INDENT]

Two questions: 
[LIST=1]
[*]If I use both **top** and the **System Manager** on my desktop machine, they show *very* different numbers for the amount of RAM used. Which one is more accurate?
[*]For the different processes that are being summed to arrive at the "812024k used" (by **top** above), how can I get an *itemized* list that shows how much RAM each one is using?

[/LIST]
I have tried **ps aux**, but the numbers do not seem to "add up."

thanks.

---

### Post by bingoUV on 2008-05-04
> **kabanta said:**
> I am trying to figure out the *details* of RAM usage for a Hardy server installation. The solution needs to be *terminal based*, rather than, say, the gui-based &quot;System Monitor.&quot;

If I run **top**, something like the following is *summarized*:
[INDENT]Mem:   1026136k total,   *812024k used*,   214112k free[/INDENT]Two questions: 
[LIST=1]
[*]If I use both **top** and the **System Manager** on my desktop machine, they show *very* different numbers for the amount of RAM used. Which one is more accurate?
[*]For the different processes that are being summed to arrive at the &quot;812024k used&quot; (by **top** above), how can I get an *itemized* list that shows how much RAM each one is using?
[/LIST]
I have tried **ps aux**, but the numbers do not seem to &quot;add up.&quot;

thanks.

 Processes share memory so it will not add up. Read [http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419).

---

### Post by kabanta on 2008-05-04
> **bingoUV said:**
> Processes share memory so it will not add up.

Then perhaps I am not using the correct terminology. *SOMETHING* "adds up" to provide a number for "memory used" (whether I use **top** or **free**, as they suggest in the link you posted). All I want to know is: how do I find an itemized list (that shows memory usage) for the elements that are added together for the number displayed for "memory used."

---

### Post by NightwishFan on 2008-05-04
```
free -m
```
That is a good command to see total ram in easy to read mb. The line +/- buffers/cache is the one you want to pay attention to.

---

### Post by kabanta on 2008-05-04
> **NightwishFan said:**
> ```
free -m
```
That is a good command to see total ram in easy to read mb. The line +/- buffers/cache is the one you want to pay attention to.

Yes, thanks. Any tips for how to see the individual elements that make up that total ram usage?

---

### Post by bingoUV on 2008-05-04
> **kabanta said:**
> Then perhaps I am not using the correct terminology. *SOMETHING* &quot;adds up&quot; to provide a number for &quot;memory used&quot; (whether I use **top** or free</b>, as they suggest in the link you posted). All I want to know is: how do I find an itemized list (that shows memory usage) for the elements that are added together for the number displayed for &quot;memory used.&quot;

 What do you want the elements to be? 

1. Processes : Not possible. As explained in the link, processes share memory. If you count this shared memory against each process and sum all, you end up with more than the really utilized memory. If you do not count it, you end up with less.  

2. How the memory is used? : See the file /proc/meminfo. This itemization includes swap too.

 You could also keep adding 1 until you reach the total utilized memory. All the 1s that you added will [add up] to the total utilized memory.

---

