---
title: "[SOLVED] massively unbeleivably huge text files"
date: 2008-07-06
forum: General Help
---

### Post by 0perator on 2008-07-06
i  have a massive text file (over 3gb) i know about the head command but i am not sure how to get it to sice the first 20mb then the next 20...


thanks.

---

### Post by ChameleonDave on 2008-07-06
> **0perator said:**
> i  have a massive text file (over 3gb) i know about the head command but i am not sure how to get it to sice the first 20mb then the next 20...


thanks.

If I've understood correctly, you want to segment this large file into several smaller ones for some reason.  Is that right?

---

### Post by 0perator on 2008-07-06
> **ChameleonDave said:**
> If I've understood correctly, you want to segment this large file into several smaller ones for some reason.  Is that right?

affirm :D

sorry :$

---

### Post by ChameleonDave on 2008-07-06
I've never used it before, but *csplit* looks like it could do the job.

```
**csplit** BigFile.txt  1000 {10}  -f Chunk  -b %02d.txt
```

That will go through the file until the thousandth line, and put it into a new file called Chunk00.txt, and then carry on doing that again ten times with different chunks, and then it dumps the rest in Chunk11.txt.

Not perfect, I know, but that's my initial stab at a solution.

```
**man** csplit
```

Look at the manual page for the command.  It can be refined to make it search for specific headings in the text and split at that point.

---

### Post by 0perator on 2008-07-06
ah cool, thanks seems to be working, :D

---

### Post by ChameleonDave on 2008-07-06
> **0perator said:**
> ah cool, thanks seems to be working, :D

OK, great.  Did you manag/e to read the manual and make it split your file by looking for strings in it?  What sort of file is it?

If it's all solved, then edit the title of the thread to put "[SOLVED]" in it.

---

### Post by 0perator on 2008-07-06
ok i'll do that, but i hasd to go out so im just experimenting with it.. will put solved when its finished..
the text file is actually rainbow tables... only goes 1 - 9 characters so far, but if u want to use it give me a shout and i'll link you.

---

### Post by 0perator on 2008-07-06
yes it worked, i decided not to bother with them now, but at least theres a solution to a problem if anyone else has it :D

how do i mark it as solved?

---

### Post by ChameleonDave on 2008-07-06
> **0perator said:**
> yes it worked, i decided not to bother with them now, but at least theres a solution to a problem if anyone else has it :D

how do i mark it as solved?

There's a "thread tools" thingy at the top.

---

