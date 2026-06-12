---
title: "/var problems"
date: 2008-03-19
forum: General Help
---

### Post by 16777216 on 2008-03-19
When I installed this time I foolishly made the /var partition xfs.

For some unknown reason it got file system errors, I believe I have that fixed for the most part.

The thing I would like to know is can I delete the partition and remake it with another file system type (recommendations welcome) or some how "convert" it to another file system type?

I would like to do this without reinstalling, and yes, a 5000 step convoluted processes is acceptable. :)

---

### Post by chrisccoulson on 2008-03-19
Well, I think the only way to do this is to copy the contents of /var on to another partition temporarily, reformat the /var partition with chosen filesystem, then copy the contents back again.

You should do this from the live CD.

I have to stress - whatever method you use to back up the contents of /var MUST preserve file permissions and ownership, else you're going to have a headache afterwards. I suggest looking at [this]("http://ubuntuforums.org/showthread.php?t=81311") thread for backing up the whole system, and apply the same principles for backing up /var.

---

### Post by 16777216 on 2008-03-19
That was what I was thinking I should do.

Thank you.

Anyone have suggestions as to what file system to use?

---

### Post by 16777216 on 2008-03-19
That worked now I just need to make a new UUID for sda6 for fstab.

---

