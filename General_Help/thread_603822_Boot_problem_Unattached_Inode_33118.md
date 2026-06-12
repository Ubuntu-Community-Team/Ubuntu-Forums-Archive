---
title: "Boot problem: Unattached Inode 33118??"
date: 2007-11-05
forum: General Help
---

### Post by Locutuslaser on 2007-11-05
My daughter played with gcompris, it crasched and i could not shut it down. After Cnt-alt-backsp Ubuntu Feisty didn't respond either. Only way: shutted power off, and now i have a boot problem after file check fsck: unattached inode.
I cannot enter something, i wanted to fsck in the pre screen, no result. Only thing it did was a normal boot after contr-d, but every boot gives this inode error. [http://img46.imageshack.us/my.php?image=vastog6.jpg](http://img46.imageshack.us/my.php?image=vastog6.jpg)
The error is in my home folder ext2 partitioned. Can i do fsck in terminal when ubuntu is running?  

With:

# fsck /dev/hda2

and after repair:

> #mount -m -o remount, rw /

Or can i solve this in an other way?

Btw i should change ext2 to reiserfs with gparted, reiser and ext3 logges when it's used. But first the error solving.

---

### Post by dcstar on 2007-11-05
> **Locutuslaser said:**
> My daughter played with gcompris, it crasched and i could not shut it down. After Cnt-alt-backsp Ubuntu Feisty didn't respond either. Only way: shutted power off, and now i have a boot problem after file check fsck: unattached inode.
I cannot enter something, i wanted to fsck in the pre screen, no result. Only thing it did was a normal boot after contr-d, but every boot gives this inode error. [http://img46.imageshack.us/my.php?image=vastog6.jpg](http://img46.imageshack.us/my.php?image=vastog6.jpg)
The error is in my home folder ext2 partitioned. Can i do fsck in terminal when ubuntu is running?  

With:

# fsck /dev/hda2

and after repair:

> #mount -m -o remount, rw /

Or can i solve this in an other way?

Btw i should change ext2 to reiserfs with gparted, reiser and ext3 logges when it's used. But first the error solving.

In a terminal:

```
sudo nano /etc/default/rcS
```

Change FSCKFIX= from "no to "yes" and save the file.

When you boot up any fsck should run and now fix any problems automatically.

---

