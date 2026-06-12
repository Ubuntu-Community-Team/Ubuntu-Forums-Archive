---
title: "how to defrag ext3 partitions"
date: 2008-03-01
forum: General Help
---

### Post by onemanclapping on 2008-03-01
hi,

is there any tool for me to defrag my ext3 partition?

thanks in advance

---

### Post by wh33t on 2008-03-01
I'm not 100% on this. But I don't beleive you need to defrag ext3.

---

### Post by LaRoza on 2008-03-01
You don't need to defrag EXT3.

---

### Post by Fixman on 2008-03-01
Only NTFS and FAT32 need defragmentation.

---

### Post by wh33t on 2008-03-01
Thanks for confirming.

"Fragmentation" I beleive is a bug or design flaw in the the NTFS and Fat32 file system. I beleive ext3 and most other opensource File systems "defragment" on the fly if you want to think about it that way. Basically they are constantly ordering stuff in the right place.

I beleive Vista is trying to do something similar.

---

### Post by Fixman on 2008-03-01
> **wh33t said:**
> Thanks for confirming.

"Fragmentation" I beleive is a bug or design flaw in the the NTFS and Fat32 file system. I beleive ext3 and most other opensource File systems "defragment" on the fly if you want to think about it that way. Basically they are constantly ordering stuff in the right place.

I beleive Vista is trying to do something similar.

It is not a bug, its just from the way its done.
Think it like this:

```

You have many programs.
Programs can weight more or less.
You delete a program that was sized 2.
You create a program of 1 of size.
NTFS creates it at the end of all.
Ext3 Creates it where the file sized 2 used to be.

Defragmentation means "deleting" all programs and putting them one to the side of another.

```

---

### Post by wh33t on 2008-03-01
Lol. that very much sounds like a design flaw to me.

---

### Post by JohnLM_the_Ghost on 2008-03-17
hmm, I was also wondering about defragmenting ext3...


Still I don't understand how does ext3 works around fragmentation problem.
Could one explain or link to some info? Thanks!

---

### Post by Ub1476 on 2008-03-17
[Wikipedia]("http://en.wikipedia.org/wiki/Defrag")

---

### Post by bodhi.zazen on 2008-03-17
> **JohnLM_the_Ghost said:**
> hmm, I was also wondering about defragmenting ext3...


Still I don't understand how does ext3 works around fragmentation problem.
Could one explain or link to some info? Thanks!

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)


Every file system has some fragmentation, the question is how much and is it enough to affect performance.

Fragmentation is not a problem on Linux system unless your hard drive gets full, and then the solution is to free up space or add additional storage.

---

### Post by JohnLM_the_Ghost on 2008-03-17
Thanks! Though I was able to dig up some info by myself already.

From both sources It was clear that fragmentation on ext3 is negligible and there is no real defragmenting utility for it anyways.

---

