---
title: "What constitutes a &quot;write&quot;?"
date: 2007-03-26
forum: General Help
---

### Post by newbie22 on 2007-03-26
Some memory hardware says that it can be written up to x amount of time.  It got me thinking, what constitutes as a "write"?

1. If I were to copy 100 files into the HDD at once, is that 1 write or 100 writes?

2. If a folder that contains 100 files were to be copied into the HDD, is that 1 write or 101 writes?

3. If I were to burn something into a CD, be it 1 file or 100 files, it would be counted as just 1 write, right?

---

### Post by josephus on 2007-03-26
Don't know for sure but my guess is that you can rewrite to a physical location x times.  The files in the first example all occupy different physical addresses and therefore would constitute 1 write to each of those locations.  If you were to copy over those files then you that would be a second write.

---

### Post by newbie22 on 2007-03-28
Thanks for replying.  But I was looking for a more technical answer than a guess.  Anyone understand how the write works?

---

### Post by insane_alien on 2007-03-28
it reffers to writing a bit to a memory address.  so every available bit on the memory device has a certain amount of writes available before its likely to start failing.
 
if the 100 files added up to 100 MB then there would be a write operaton for every single bit but it would be a write to the same number of addresses. if the addresses had 100 writes possible then you would have 800M addresses with 99 writes left and the rest would still have 100 left. its a bit over simplified but its adequate.

---

