---
title: "Partition question"
date: 2007-05-20
forum: General Help
---

### Post by geovino on 2007-05-20
I have used GParted to delete some old partitions on the hdb drive. 

I'm having trouble adding the Unallocated segment (5.85 gb) to the /dev/hdb5 partition (30.85 gb) How do I combine the two so all I have is a 37 gb hdb5 partition and a 2 gb swap file?

Here's a screen shot:

---

### Post by ajmorris on 2007-05-20
> **geovino said:**
> I have used GParted to delete some old partitions on the hdb drive. 

I'm having trouble adding the Unallocated segment (5.85 gb) to the /dev/hdb5 partition (30.85 gb) How do I combine the two so all I have is a 37 gb hdb5 partition and a 2 gb swap file?

Here's a screen shot:

You should be able to right click on the unallocated space and click 'move'. move it to behind the EXT3 partition, then resize the ext3 partition to take up the unallocated space.

---

### Post by geovino on 2007-05-20
When I right-click, the only option is NEW. No Move option. Should I just delete all the partitions and let the installer format the install on the whole hdb drive?

---

### Post by BitTorrentBuddha on 2007-05-20
I don't believe ext3 supports "moving" partitions around, or appending more space at the beginning of a partition. You're only options for that space are to either increase the size of the partition to the left or make a new partition there.

---

