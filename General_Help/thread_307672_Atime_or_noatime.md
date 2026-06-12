---
title: "Atime or noatime?"
date: 2006-11-26
forum: General Help
---

### Post by Owdy on 2006-11-26
Does anyone know what will i miss if i use 'noatime' in fstab? Does it really make my machine faster? Is there any downsides?

---

### Post by RAOF on 2006-11-26
Your files won't get a "last read" time.  It does make file reads (marginally) faster, because it doesn't have to update the atime field.  Whether or not you'll see any downside depends on whether you'd ever want to know a file's "last accessed time".  I can't, off the top of my head, think of any reason you'd want that :).

---

### Post by dcstar on 2006-11-27
> **RAOF said:**
> Your files won't get a "last read" time.  It does make file reads (marginally) faster, because it doesn't have to update the atime field.  Whether or not you'll see any downside depends on whether you'd ever want to know a file's "last accessed time".  I can't, off the top of my head, think of any reason you'd want that :).

One value if the "last accessed time" is used is to determine if you have files on your system that are never (or rarely) used, or find the ones used more frequently than others.

In corporate environments you can sort by this field and determine if you are wasting (valuable) disk space storing things that are redundant, or may be better stored on some other medium (or determine if frequently accessed files should be placed together for optimal disk performance etc.)

In the average Linux "user" installation, this sort of thing is next to useless, and because the atime feature causes a inode write for every read, it actually increases the risk of any filesystem problems by increasing the amount of writes than if noatime was set (as well as the negative performance "hit" by forcing these writes).

---

### Post by Owdy on 2006-11-27
So you recommend noatime?

---

### Post by dcstar on 2006-11-27
> **Owdy said:**
> So you recommend noatime?

I have noatime on all my fstab entries.

---

### Post by Owdy on 2006-11-28
Ok, thanks!  How about syncronising. I use Rsync to backup my /home folder, does this mess that up somehow?

---

### Post by RAOF on 2006-11-28
It shouldn't, because the last **write** time will still be updated.  And rsync shouldn't care whether or not the file has been read since it was last syncd.

---

### Post by Owdy on 2006-11-29
Ok, thank you!

---

### Post by aysiu on 2006-11-29
I just switched to *noatime* and rebooted... no noticeable performance difference on my machine.

---

