---
title: "Hibernating - Swap file too small?"
date: 2007-10-13
forum: General Help
---

### Post by watermark on 2007-10-13
I've seen posts similar to this, but not answering my question.

When I attempt to hibernate my desktop, I get a "not enough swap space" error message.  Seems more or less straight forward, I need more swap...but how much more swap do I need?  Before this episode, I didn't realize that hibernate/suspend needed swap space to work, or I would have stuck with the 1.5x ram for the swap, but as I have 1Gig memory, I chose to keep my swap smaller.  Here's my "free"  output.
```

             total       used       free     shared    buffers     cached
Mem:       1035776     689464     346312          0       7188     188988
-/+ buffers/cache:     493288     542488
Swap:      1068272      78640     989632
```

Will the extra 500mb really solve my problem?

---

### Post by Pumalite on 2007-10-13
Hibernation in laptops require /swap to be equal to RAM

---

### Post by watermark on 2007-10-13
As you can see, my swap is 3mb larger than my ram.

---

### Post by Pumalite on 2007-10-13
You should be OK. then.

---

### Post by FuturePilot on 2007-10-13
I think the problem is that you are already using some swap space which is being taken into consideration. And therefore, the amount of free swap that is left is below your total RAM. So yes, I think you need some more swap. They usually say 2x your RAM.

---

