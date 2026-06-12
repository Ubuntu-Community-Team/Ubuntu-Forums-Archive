---
title: "Why we can't make 4 primary partition in harddisk."
date: 2008-04-04
forum: General Help
---

### Post by kapilagarwal61 on 2008-04-04
hi all,

Can anyone tell me why we can't make 4 primary partition in harddisk.
what is the reason?

---

### Post by sekinto on 2008-04-04
You can make 4.

---

### Post by angry_johnnie on 2008-04-04
Well, you can't make more than four.

The Partition Table is divided into four sections and hence the limitation of four Primary Partitions. Its the design of the Partition Table that causes the limitation.

To work around this limitation, you can create three primary partitions and an extended one.  You may then divide that extended partition into however many logical partitions you like.

However, some operating systems, like Solaris or FreeBSD, need to be installed on a primary partition --although, I think NetBSD can be installed on a logical partition.

For the most part, logical partitions should do the trick, unless you're dealing with really greedy operating systems :-).  If you want to try lots of different Linux flavors, then you don't really need more primary partitions.  Just make one big extended partition and throw 'em all in there.

---

