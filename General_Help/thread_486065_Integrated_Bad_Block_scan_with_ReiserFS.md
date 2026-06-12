---
title: "Integrated Bad Block scan with ReiserFS"
date: 2007-06-27
forum: General Help
---

### Post by Yoooder on 2007-06-27
Hey, I have an old and heavily used 250gb drive that I think has some bad blocks on it.  The whole thing is occupied by a single reiserfs partition.

Does reiserfsck have any kind of bad-block scanning abilities, or anything else in the reiserfstools package for that matter?  I did some poking around this morning and was left with the impression I'll need to use the "badblocks" program to generate a list of the bad blocks, then reiserfsck to import the list--is that right?

---

