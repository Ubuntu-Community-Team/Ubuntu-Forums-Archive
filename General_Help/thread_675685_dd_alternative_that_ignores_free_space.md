---
title: "dd alternative that ignores free space"
date: 2008-01-22
forum: General Help
---

### Post by Meson on 2008-01-22
I'm currently imaging a 230 gb hard disk with dd.  It's taking forever!  And unfortunately I couldn't make a direct copy to the new disk so I have to save it to an external medium first.  

This isn't a backup, it's just a one-time operation, so I'm not worried about using gzip to compress it.

I'm just wondering if there is a faster way to image a large hard drive even if there is only a small amount of data on it.  For example, I'm only using 60 out of 230 gb.

---

### Post by Aearenda on 2008-01-23
Detecting free space is file-system dependent, so you have to use a tool that is aware of file systems. For Windows systems I use ntfsclone as part of clonezilla ([http://clonezilla.sourceforge.net](http://clonezilla.sourceforge.net)) and for Linux partimag, also managed by clonezilla (but see [http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html](http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html)).

---

### Post by Meson on 2008-01-23
The reason I wanted to avoid partimage is because it looked like a pain to do a full disk backup.  I'm copying a dell hard disk with a recovery partition and some other stuff so it's a little messy to do partition by partition.

---

### Post by shaggy999 on 2008-01-23
If you tell it to backup the whole disk it will backup all of the partitions. You don't have to manually do each partition. And it will still skip freespace. I've used clonezilla to duplicate a dell system dual-boot w/ Dell's secret partition, too, and it was a cinch. Very fast, too.

---

### Post by Meson on 2008-01-23
Hmm, yeah Clonezilla is perfect.  I'm not sure why all my searching only turned up dd and partimage.

---

### Post by Aearenda on 2008-01-23
There's g4l as well, but I have never used that so I don't know how it compares.

---

### Post by Meson on 2008-01-23
g4l looked like a pain.

btw - clonezilla didn't quite work.  I think it has something to do with one of the partitions being a new ntfs filesystem.  I booted from the ubuntu live cd and am now trying partimage.

---

### Post by Meson on 2008-01-24
In the end, g4l, parted magic, partimage, and clonezilla all failed to copy the ntfs (I presume 3G) partition.

I needed to use dd, it took quite a while on a 230 gig drive, but it worked.

---

### Post by Aearenda on 2008-01-24
Thanks for the update, and sorry you had to do it the long way!

Was your NTFS partition created by Vista?

---

