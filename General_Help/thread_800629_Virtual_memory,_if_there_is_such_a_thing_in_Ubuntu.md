---
title: "Virtual memory, if there is such a thing in Ubuntu"
date: 2008-05-20
forum: General Help
---

### Post by sgcharest on 2008-05-20
Does Ubuntu have a control for what Win calls "virtual memory?"  If so, how can I change it?  Otherwise, am I pretty well stuck with the 2gb of ram I have (not bad but not great).  Thnanks in advance.

sgc

---

### Post by p_quarles on 2008-05-20
Yes, it does. It's called the "swap file," and if you performed a normal installation, you already have one. 

That said, normal desktop operations on a Linux box with 2 gigabytes of RAM will rarely ever need to use swap space. This is a good thing, though, as swap as considerably slower than physical memory.

EDIT: I should add that you are actually likely to get better performance -- given the amount of RAM you have -- by setting the system to use swap space very frugally.

---

### Post by darco on 2008-05-20
Its called SWAP and I believe Ubuntu automaticaly creates a swap partition when you install it. Check Resources under System Monitor..I have 2 gig ram and the swap equals that size. As far as resizing it, I guess possibly g-parted or any other partition program could enlarge it but not sure if thats advisable.

darco

---

### Post by sgcharest on 2008-05-20
According to my system monitor it is not using any swap at all.  That's just with Firefox and a calendar running.  I am curious what will haoppen when I load Second Life (the Debian edition is working pretty well).

---

