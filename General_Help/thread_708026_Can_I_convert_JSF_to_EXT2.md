---
title: "Can I convert JSF to EXT2?"
date: 2008-02-25
forum: General Help
---

### Post by joemok on 2008-02-25
I accidentally installed ubuntu using JSF filesystem. And I find it much slower than EXT2 in my SDHC of eeepc.

If I convert it to EXT2, e.g. by gparted, is the danger serious?

---

### Post by bodhi.zazen on 2008-02-25
I suggest you use a journaled file system, ie Ext3 (or reiserFS or XFS)

Yes you can easily convert the partition by formatting it. THIS WILL ERASE ALL THE DATA on the partition, so back up any data you want to keep to another partition / CD/DVD first, then restore it.

---

### Post by joemok on 2008-02-26
Can I just do the conversion without formatting?
If I had to resort to formatting, how can I backup all the files, the whole system, and then put it back after formatting?
Thank you.

---

### Post by bodhi.zazen on 2008-02-26
No, no way to convert without formating.

If you are talking about / , best re-install

You can put /home on it's own partition.

And last, in my experience, I do not find changing file systems to be all that big a performance boost. So are you sure it is the file system and not something else that is slowing you down ?

---

### Post by joemok on 2008-02-26
yes, i am quite sure.
 Previously ubuntu 8.04 was install on my SDHC with filesystem ext 2. And due to some problems i formatted it and changed jfs accidnetally, and now it is not less responsive. 
I doubt if jfs recorded logs too often which slows down SDHC dramatically.

---

### Post by articpenguin on 2008-02-26
umm JFS is journalled and its not paranoid about the journal as ext3 is. 

also JFS stands for Journalled File System

---

