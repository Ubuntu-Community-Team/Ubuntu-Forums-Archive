---
title: "quick question"
date: 2007-11-23
forum: General Help
---

### Post by fiddilydee on 2007-11-23
complete noob following instructions for a manual partition and install. My instructions don't say how to format the /home drive? (nfts, ext3? etc) What do I use?

---

### Post by Ehtetur on 2007-11-23
Pretty gutsy move for a noob...
You want your linux partition(s) to be ext3

---

### Post by fiddilydee on 2007-11-23
Yeah I know but Vista is pissing me off and I have read lots of good things about ubuntu. I know alot about windows but nothing about ubuntu. I know it can do everything I use my computer for easily and I still have windows disk if I nee it (i hope not) although installation has been anything but smooth, I have alot of patience for this type of thing.

---

### Post by fiddilydee on 2007-11-23
this is what i did

Create one partition that is 10 gig and mount that as root and as ext3.
Create one partition that is 1 gig and mount it as swap - swap has it's own file system.
Create one partition from the rest of the free space and mount it as /home.

this is what it says No root file system is defined

---

### Post by Zimmer on 2007-11-23
If you intend to Dual boot
Explanation of possible schemes..
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
and the guide on How to
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Should be all you need to know . They are the two resources I used for partitioning and installing.

---

### Post by bmwerks on 2007-11-23
use this tutorial site its what i use when i was installing gutsy it will walk you through everything. it really helpful.

:) sorry forgot the website-> [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by geirha on 2007-11-23
> **fiddilydee said:**
> Create one partition that is 10 gig and mount that as root and as ext3.


You want to mount it as /  which is commonly referred to as "root"

---

