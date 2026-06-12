---
title: "partitioning the mounted drive"
date: 2006-08-03
forum: General Help
---

### Post by NonaWeisbaum on 2006-08-03
I've been looking for a couple days but I can't seem to find an answer anywhere. 
I would like to partition my Linux drive to give Windows some space so I can reinstall World of Warcraft. Gparted puts the little lock next to / cos it's mounted and whatnot and I can't add a partition. Is there a way around this or is this something I'll have to try to do from Windows? Could that mess up my Linux since Windows doesn't recognize the file system?

:-k

---

### Post by Polygon on 2006-08-03
can qtparted partiton drives that have already been partitioned? (kinda like partiton magic for windows... if you know it)

anyway if qtparted can partition drives without formatting the whole disk and then doing all the partitions over again, then simply just boot from a live cd (i think knoppix has qtparted on it, im not sure about ubuntu live cd though) and then run qtparted from there.

---

### Post by RAOF on 2006-08-03
> **NonaWeisbaum said:**
> ...Could that mess up my Linux since Windows doesn't recognize the file system?

:-k

**Yes**.  If you need to shrink the root partition, you'll need to do it with a tool that understands the filesystem (EXT3, probably).  You should be able to create partitions on a drive with mounted partitions on it, but you generally can't shrink mounted partitions.

As polygon says, you probably need to use a LiveCD to do your partitioning.  The Dapper desktop/install CD should do fine, or if you don't have one of those lying around, I personally like the [system rescue cd]("http://www.sysresccd.org/Main_Page")

---

### Post by NonaWeisbaum on 2006-08-04
Thanks!

---

