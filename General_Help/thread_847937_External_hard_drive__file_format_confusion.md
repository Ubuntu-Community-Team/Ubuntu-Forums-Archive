---
title: "External hard drive:  file format confusion?"
date: 2008-07-03
forum: General Help
---

### Post by atorch on 2008-07-03
Hi,

Here're the contents of a little text file ("/media/disk/File system madness.txt") living on my external hard drive:

"Properties tells me this drive is formatted as:
<< ext3 >>

GParted tells me this drive is formatted as:
<< ext2 >>

...which is it?"

//Edit:

Also, Properties tells me 81.2 Gigs of space on this disk are used; however, I've only put 73.6 Gigs of data on it, leaving 7.6 Gigs of... overhead?  What?

---

### Post by atorch on 2008-07-05
Bump up my post.

Anyone?

---

### Post by chrisccoulson on 2008-07-05
Basically, EXT3 = EXT2 + journal

You can mount an ext3 partition as ext2, but you lose the journalling capabilities. Likewise, you can mount an old ext2 partition as ext3, and it will get a journal.

As for the space, could you post the output of 'df -h' with the drive mounted

---

