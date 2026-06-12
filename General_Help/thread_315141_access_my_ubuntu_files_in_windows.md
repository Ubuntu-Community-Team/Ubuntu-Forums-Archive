---
title: "access my ubuntu files in windows?"
date: 2006-12-08
forum: General Help
---

### Post by Jack of Fables on 2006-12-08
is there a way that i can mount my ubuntu partition while in windows so that i can have access to all my files? was wondering because i did it in my sabayon live cd. looking for simple instructions or an app or something easy to use.

---

### Post by bodhi.zazen on 2006-12-08
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Jack of Fables on 2006-12-08
thanks!
even better than what i used in sabayon, works great!

---

### Post by azelter on 2006-12-08
I would advise against this for security reasons. If windows mounts your linux partition, the a windows virus can affect you linux o/s too.

---

### Post by bodhi.zazen on 2006-12-08
> **azelter said:**
> I would advise against this for security reasons. If windows mounts your linux partition, the a windows virus can affect you linux o/s too.

That is just plain false. Windows viruses can not affect linux.

---

### Post by Azakus on 2006-12-08
Or you could make a share partition which can be seen by both using FAT32 as the partition type. I have a 40gb one I store my movies and music on.

---

### Post by azelter on 2006-12-13
I would go for the last option (install a shared drive).
As for what I said before being false. It isn't. If the windows virus decides it will wipe all the disks - in windows - and one of those drives is your linux partition (mounted in windows) then your linux partition will be damaged/wiped/whatever too. You never need to boot in to linux to damage the linux instalation if it is mounted in windows. Do you disagree?

---

### Post by meng on 2006-12-13
> **azelter said:**
> I would go for the last option (install a shared drive).
As for what I said before being false. It isn't. If the windows virus decides it will wipe all the disks - in windows - and one of those drives is your linux partition (mounted in windows) then your linux partition will be damaged/wiped/whatever too. You never need to boot in to linux to damage the linux instalation if it is mounted in windows. Do you disagree?
I don't disagree, but couldn't a windows virus wipe a partition even without recognizing its filesystem? Hence I don't see that fs-driver increases the risk significantly. But it's good to be careful!

---

### Post by newlinux on 2006-12-13
> **meng said:**
> I don't disagree, but couldn't a windows virus wipe a partition even without recognizing its filesystem? Hence I don't see that fs-driver increases the risk significantly. But it's good to be careful!

Yes it could, but it would be harder - another layer to make it difficult for the virus.

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-13
you would have to use a shard fat32 partion or another file system that both operating systems can read right to
ubuntu runs on ext3 and can read ntfs but not right it
windows cant read or right ext3 <- i think not to shur, but the other guys are right it wouldn't be as secure doing it that way widows would mess stuff up for shur.

---

### Post by meng on 2006-12-13
> **<<joe>> said:**
> you would have to use a shard fat32 partion or another file system that both operating systems can read right to
ubuntu runs on ext3 and can read ntfs but not right it
windows cant read or right ext3 <- i think not to shur, but the other guys are right it wouldn't be as secure doing it that way widows would mess stuff up for shur.
Windows can read ext3 fine with fs-driver, as others have said.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-05-24
not really i did some more reading on this and it treats it like an ext2 file system that makes problems if shut down incorectly

---

