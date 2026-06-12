---
title: "Linear software raid disk died"
date: 2007-09-09
forum: General Help
---

### Post by radams58 on 2007-09-09
First and foremost.  I am an idiot who does not backup NEARLY often enough.

Mea culpa and lesson learned.

That said, ONE of the drives of my old linear array is still functional.  It's an ext3 filesystem.  Is there anyway to salvage the data?

Thanks, Rob

---

### Post by kidders on 2007-09-10
Hi there,

Using linear RAID is suicide, unfortunately. All it really achieves is a doubling (at least) of the probability of losing your data ... and since RAID arrays can be quite large, there's lots more data to lose, in addition to the performance penalty you pay for using it in the first place :-( To make matters worse, there's no way to be sure that, after prolonged use, any of your files are stored in their entirety on a single disk. So, depending on how long you've been using the array for, fragmentation may prevent you recovering much of your data.

Which disk has failed is also important ... especially if you had a lot of free space in the array. If, for the sake of example, the "first" device in a linear array composed of two 500GiB disks were to fail after a few weeks of use, and there were 0.75TiB of free space on the array's filesystem, one would expect none of the data to be salvageable, since it would all have been stored on the dead disk.

I suppose how much data you can get back is all down to circumstance. It's at least theoretically possible that you could recover *all* of it ... or equally, little or none of it. I would suggest...
[LIST]
[*]Try to get a handle on some of the details about exactly what failed, what the nature of the failure is, and how it relates to your files. Your post doesn't indicate, for instance, if the "dead" disk really is dead (if you know what I mean), or perhaps just a little corrupted.
[*]If you feel there is a chance some of your data may be recoverable, you could start exploring some forensic data recovery applications, to see if they can do anything for you.[/LIST]It may be, for example, that the dead disk is failing simply because a small part of it has some physical damage. In that case, you could conceivably be in a position to recover almost all of your data, simply by dumping the contents of the damaged disk onto a fresh one.

Unfortunately, your post doesn't give anything like enough detail to make an educated guess about your chances, or what to do next, but I hope this helps a little.

---

