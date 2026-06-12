---
title: "Why is there 5GBs missing?"
date: 2006-07-07
forum: General Help
---

### Post by CGW on 2006-07-07
I have an 80GB HD installed in my Dell Inspiron 6000.  10GB goes to WinXP which should leave 70GB.  Right?  However, Ubuntu (Dapper) says I only have 64.53GB remaining for the install/swap.  Why?  What happened to the +/- 5.5GB?

I have Ubuntu using 62.53GB with a 2GB swap (I have 1GB RAM).

Unless I'm just screwing up the math--Where's my 5.5GB??

BTW-when I run the partitioner it says there is no free space.  It also claims that the 3 existing partitions (Win/ext3/swap) are the only partitions there also.

I did a search for this issue but didn't find an existing thread that fit my circumstances.

Thanks in advance for any help.

Chris

---

### Post by aysiu on 2006-07-07
It has do with the way bytes are counted. There are two ways to count, I think.

**Edit**: Ah, here we go. Turns out there are three.
[http://en.wikipedia.org/wiki/Gigabytes](http://en.wikipedia.org/wiki/Gigabytes)

In case you're too lazy to read the whole thing, here's one relevant portion: > As of 2006, most consumer hard drives are defined by their gigabyte-range capacities. The true capacity is usually some number above or below the class designation. Although most hard disk manufacturers' definition of GB is 1,000,000,000 bytes (only computer memory has a natural inclination towards units that are powers of 2), most computer operating systems use the 1,073,741,824 byte definition. This distinction can cause confusion.

---

### Post by CGW on 2006-07-07
Gotcha.  Thanks.

I knew that--but I was under the impression there were compensations made to prevent 'confusion.'  Guess not ;)

---

