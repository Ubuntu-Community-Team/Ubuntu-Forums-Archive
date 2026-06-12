---
title: "Shrink /-partition and expand /home-partition?"
date: 2007-05-09
forum: General Help
---

### Post by Vinze on 2007-05-09
Hey, 

My hdb is partitioned with a /-partition, a /home-partition and a swap-partition. However, when I installed Xubuntu a long time ago, I did not set them the correct size, meaning that my /home-partition now is full and my /-partition almost empty. I wanted to shrink the /-partition with Gparted from the LiveCD, which I could do, however, I could not give the created free space to /home . How should I do it? Thanks.

---

### Post by Vinze on 2007-05-09
Please, it is now getting extremely annoying as my settings won't load, so my panels look all messed up. Not to mention that I cannot save anything :( I really need help here...

---

### Post by Xeor on 2007-05-09
This might help you:

[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

I still advice you to have an external hard-drive to do a backup first because whatever it says in the title of this page, there is an old tune that was saying you might loose data. :guitar:

---

### Post by Jonne on 2007-05-09
You can't let a partition grow to the start (to the left). So you'll have to put your stuff on an external hd, delete your /home partition, and recreate a new one after you've shrunk your / partition.

If you don't have an extra HD (and you don't want to burn everything on cd's), you'll have to basicly shrink your / partition, create a new partition between the / partition and what's /home now, and copy your stuff over from old home to new home. If you can't put everything you have in one shot between / and /home, just copy over as much as possible, use the new freed space after /home to create a new partition after shrinking /home, copy your stuff from /home to the partition after /home, then delete your /home partition, grow the partition that is now right behind / until you can't grow it any more, move stuff from the last partition to your new /home, etc.

It's a pain, it will wear your disk out, but it's doable (I went through the same process once ;) ).

But I'd strongly suggest you get an external HD, that way you can do backups and offload crap too.

---

### Post by Vinze on 2007-05-09
> **Jonne said:**
> You can't let a partition grow to the start (to the left). So you'll have to put your stuff on an external hd, delete your /home partition, and recreate a new one after you've shrunk your / partition.

If you don't have an extra HD (and you don't want to burn everything on cd's), you'll have to basicly shrink your / partition, create a new partition between the / partition and what's /home now, and copy your stuff over from old home to new home. If you can't put everything you have in one shot between / and /home, just copy over as much as possible, use the new freed space after /home to create a new partition after shrinking /home, copy your stuff from /home to the partition after /home, then delete your /home partition, grow the partition that is now right behind / until you can't grow it any more, move stuff from the last partition to your new /home, etc.

It's a pain, it will wear your disk out, but it's doable (I went through the same process once ;) ).

But I'd strongly suggest you get an external HD, that way you can do backups and offload crap too.

I was just following Xeor's guide (which looked very helpful, thanks!) but this is a very smart solution (why couldn't I think of that myself? ;) ), and you're just in time so I haven't done anything yet. I'd love to have an external HD to backup my stuff to but funds are low at the moment ;)

---

