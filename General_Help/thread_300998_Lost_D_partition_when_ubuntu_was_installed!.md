---
title: "Lost D: partition when ubuntu was installed!"
date: 2006-11-16
forum: General Help
---

### Post by MaestroS on 2006-11-16
When I was installing Ubuntu, it showed me FOUR partitions (when I had only 2 [C: and D:]. It confused me, and I choosed one of those, and after installation, I logged in to Windows, and ... BUMP! D: partition does not exists.

In "Computer Management" panel, there is wrote: "... - Unknown Partition"...

How can I remove Ubuntu and get back my disk?! 
It has 20gb of important school data!

---

### Post by Jongi on 2006-11-16
Get into ubuntu and type **sudo fdisk -l** and paste the output here.

---

### Post by MaestroS on 2006-11-16
But I can't access Ubuntu, because it wont load after installation... I tried install again, and BUM! Windows can't see D: partition, cause I changed (and probably formated) file system...

Any solutions to get it back ... ?

---

### Post by Jongi on 2006-11-16
So when you turn on your computer it doesn't show a bootloader but goes staright into Windows?

---

### Post by MaestroS on 2006-11-16
No, It wants me to choose between ubuntu and windows, but when I'm choosing windows, D: cannot be detected by Win XP... But I want to get it back!

and Ubuntu wont load... Im gonna die if I dont get this disk back... it will destroy my future... there was too much of projects to school I needed to pass...

---

### Post by KaeseEs on 2006-11-16
The bad news first:  Windows giving an 'unknown partition' error typically means that the partition is formatted to a filesystem Windows doesn't know how to read (eg ext3).  It looks like you waxed your partition.  

For good news, there is some hope.  Acquire a LiveCD of Ubuntu or Knoppix, and you may be able to at least read the partitions.  Once you've got one of said CDs, post here again for instructions on how to take a look into your problem.  You probably installed Ubuntu from a LiveCD, so you should be able to boot from that CD again.

In the mean time, look for a data recovery firm.  If you did reformat the partition, most of it was probably reformatted to empty space, and at least that should be recoverable.

---

### Post by Jongi on 2006-11-16
There are also Windows apps which are available to recover deleted data or formatted partitions. The reputable ones don't come for free.

---

