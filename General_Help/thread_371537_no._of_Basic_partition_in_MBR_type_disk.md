---
title: "no. of Basic partition in MBR type disk"
date: 2007-02-27
forum: General Help
---

### Post by I.You on 2007-02-27
Hi there.

In MBR type disk, the number of possible basic partitions is 3 or 4?
if 3, 4th partition is always extended or unused?

Please give me your advices.

---

### Post by yabbadabbadont on 2007-02-27
You can have 4 primary partitions total.  If you need more partitions than that, make the fourth primary partition an Extended one.  Then you can create logical partitions inside the Extended partition.

---

### Post by louis_nichols on 2007-02-27
The maximum number of primary partitions is 4. As for the other question, it doesn't mak sense in this context. Confusions may arise from the numbering system. GRUB for exaple counts partitions from 0 to 3 for primary and logical are always 5+, even id there aren't 4 primary partitions. Linux counts them differently.

If you tell us about your exact problem, someone can help.

---

### Post by I.You on 2007-02-27
Thanks a lot, yabbadabbadont and louis.

You mean that there can be 4 basic partitions only (without extended) in one system or 4th basic partition becomes extended if needed more than 4?

I would like to get the file system type of each logical partition in extended by referring partition table.
I read the MBR by raw sector reading and got the file system type of basic partitions.
However, the file system type of extended partition is just 0x05 and no more info.

If you’ve got a good idea, please advise me.

---

### Post by yabbadabbadont on 2007-02-27
You can have either 4 primary partitions OR 3 primary partitions and 1 extended partition.  (and multiple logical partitions within the extended partition.)

For more information, see here: [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

