---
title: "What happens if you use dd to clone a mounted drive?"
date: 2007-10-29
forum: General Help
---

### Post by dwasifar on 2007-10-29
If I clone a drive this way:  

dd if=/dev/sda of=/dev/sdb

...what happens if /dev/sda is mounted and active while the copy is running?

---

### Post by Prospero2006 on 2007-10-29
I do it all the time. 
I run linux on sda, and run this

dd if=/dev/sda | nc 192.168.1.110 9000


Never had a problem
Pros

---

### Post by 444 on 2007-10-29
What happens is possible filesystem corruption. Sort of like when you pull the plug on the computer without shutting down properly, except problems are even more likely. Sure I've had the power cut out plenty of times without experiencing problems, but there was one time a few years ago when my filesystem got corrupted because of that. A one in thousands chance I guess.

I'm thinking the safe way to do it would be to keep the filesystem mounted read-only while it's being done, but you can't boot far past the command line that way.

---

### Post by chrisccoulson on 2007-10-29
> **dwasifar said:**
> If I clone a drive this way:  

dd if=/dev/sda of=/dev/sdb

...what happens if /dev/sda is mounted and active while the copy is running?

I suppose that if you're writing to the mounted volume at the time of the clone, then your cloned copy could be inconsistent and corrupt. Data could be changing / moving around all the time on a mounted volume, so I'd really recommend unmounting it first.

---

### Post by dwasifar on 2007-10-30
> **chrisccoulson said:**
> I suppose that if you're writing to the mounted volume at the time of the clone, then your cloned copy could be inconsistent and corrupt. Data could be changing / moving around all the time on a mounted volume, so I'd really recommend unmounting it first.

That's how I've always done it, for precisely that reason.  I usually boot from the live CD to do it.  But I also know that it will not give an error if you issue the command on a mounted volume, so I thought maybe there was some sophisticated change tracking in there somewhere.  I guess not.  ;)  

Thanks all.

---

