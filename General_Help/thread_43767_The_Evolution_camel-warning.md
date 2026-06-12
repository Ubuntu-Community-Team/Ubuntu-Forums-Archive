---
title: "The Evolution camel-warning"
date: 2005-06-23
forum: General Help
---

### Post by Declan on 2005-06-23
Hi all,

I don't know if it's related to beagle. Yesterday the update in beagle
(from backports?) came in, and beagle began to work (a bit - it was
indexing mail from evolution and tomboy notes only).

Anyway, now evolution doesn't work at all. The window comes up, but
refuses to respond. I launched from a terminal and got the following:

es menu class init
adding hook target 'source'

(evolution:12759): camel-WARNING **: Invalid root:
'/home/declan/.evolution/mail/local/Drafts.ibex.index'

(evolution:12759): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution:12759): camel-WARNING **: block size: 1024 (1024) OK

(evolution:12759): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution:12759): camel-WARNING **: last: 6144 (6144 and size: 1024)
BAD

(evolution:12759): camel-WARNING **: flags: unSYNC
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice

Any ideas?  Fixes, workarounds?
I've googled, but I'm none the wiser.
As you can imagine, I'd like to get evolution back up.

---

### Post by Declan on 2005-06-23
Incidentally, I tried the following to no avail.
I renamed ~/.evolution as ~/.evolutionxxxx just to see what would happen.
Well... nothing happened. The program managed to generate another ~/.evolution, but suffered the same problem.  
Unless I'm mistaken, this is bad news.  

 :???:

---

