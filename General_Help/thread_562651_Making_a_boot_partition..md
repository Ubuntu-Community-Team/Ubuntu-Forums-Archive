---
title: "Making a boot partition."
date: 2007-09-29
forum: General Help
---

### Post by grungy on 2007-09-29
Hi folks,

Once again I need your appreciated help. 

I have on partition on my system: D:/

In total I have: C/ and D/

When i am installing linux i need to create 3 partitions: linux, swap and boot.
however, under linux sda1 and sd2 are already taken.
So when i am partitionning under linux i only get to get sda3 and sd4 while i need an sd5 for the boot.

My question, how can i resolve this problem.


Thank you.

---

### Post by bodhi.zazen on 2007-09-29
Well, you do not *need* a /boot partition.

But to answer you question, you can only have 4 primary partitions. You need to make an extended partition which can then have many logical partitions.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by grungy on 2007-09-29
I really need your help guys

---

### Post by bodhi.zazen on 2007-09-29
> **grungy said:**
> I really need your help guys

With what ?

As I said, you can only have 4 primay partitions and you do not need a /boot.

So you can make two primary partitions, one for / (root) and a swap 

Or you can make an extended partition and make 3 partitions, / (root), swap, and /boot

Your choice.

Do you need a link or better explanation of partitioning ?

---

