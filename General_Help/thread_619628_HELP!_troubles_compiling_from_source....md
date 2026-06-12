---
title: "HELP! troubles compiling from source..."
date: 2007-11-21
forum: General Help
---

### Post by sach87 on 2007-11-21
hi everybody!
I'm asking for some help in compiling from source...
the problem is the following:

./configure always works fine but when i run make i always get this error message:

"making all in /../..."
"leaving directory"
"make[1...2...3] nothing to be done for 'all' ".

Why is that?
Any idea?

Thx for your help!

Sach

---

### Post by cmnorton on 2007-11-21
Nothing to be done for all

means nothing needed to be made. It's not so much an error as an informational telling you why nothing was built. I've never seen the 1..2..3 before, but it looks like that Makefile is going through a lot of directories and building (or trying to build and not finding anything to build).

---

