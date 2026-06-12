---
title: "How to find/copy all non-hardlinks from a backup?"
date: 2007-02-12
forum: General Help
---

### Post by Elijah on 2007-02-12
Hi, 

I use rsnapshot for our backup scripts here, we have accumulated enough backups and we decided to burn them to a DVD disk. 

Problem is that those directories where the backups are stored in have both hardlinks & the normal files. We only needed the non-hardlinks saved so it would fit in the DVD, is there a command that could do this?

---

### Post by g3k0 on 2007-02-12
Well there really is no way to determine which file is the original one or the hard link...  Im not sure how you would find duplicate files with different names and delete one...

---

### Post by g3k0 on 2007-02-12
Well a google search found something that deletes duplicate files for linux.. I dont know if it works.  Might be risky using it....  Research the program before using it.

[http://netdial.caribe.net/~adrian2/fdupes.html](http://netdial.caribe.net/~adrian2/fdupes.html)

a thought just occurred to me that it probably just uses a standard delete which would work nicely by decrementing the count in the i-node rather than attempting to clear up the space itself... hopefully.

---

### Post by Elijah on 2007-02-13
Thanks for the reply

well, deleting might work.. but I might also delete the main non-incremental backups(?), I just needed the files updated for a certain day only. Maybe a copy command may work? just let it ignore all hardlinks?

---

