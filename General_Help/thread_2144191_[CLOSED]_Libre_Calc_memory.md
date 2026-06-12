---
title: "[CLOSED] Libre Calc memory"
date: 2013-05-11
forum: General Help
---

### Post by col48 on 2013-05-11
LibreOffice 3.5.7.2 in Precise 64bit.

I have a Calc spreadsheet containing a lot of formulae - about 500 invariant plus 30 per working row - and some of the formulae are long.  Those on each working row only refer to cells within the row.
In working with the spreadsheet, the number of working rows can vary from 1 to (in principle) a few tens of thousands (in practice <20000)
Whole groups of rows may be copied, sorted or deleted.  (By deleted, I mean what happens when using the delete key, not Ctrl with -)

I've noticed that when rows are copied or sorted the memory used increases (as expected) but when they are deleted not all of the memory seems to be reclaimed, The same thing happen after a sort completes, although the amount of memory required after the sort ought to be pretty well identical to that before.  Eventually, therefore, Calc fills the memory.  So far, I have only noticed it freezing solid, but 32-bit OpenOffice used to crash when more memory was demanded than was addressable.

I can't get onto launchpad to see if this is a known problem or whether a later version of LO behaves better.  Does anyone know the answer?

I've managed to report this as a bug on launchpad - I think!
mods:  if this justifies deleting this thread, I'll not object!

---

### Post by col48 on 2013-05-19
This turns out to be partly (largely?) due to having a large number (the default of 100) of steps specified for undo capability, and that aspect of it is not a bug.  I have an impression that this is not the whole story but the residual effect is very hard to reproduce reliably.

---

