---
title: "reiserfs damaged"
date: 2008-03-16
forum: General Help
---

### Post by hotpockets on 2008-03-16
Hi,
have a fresh install of Ubuntu gutsy on a new hard disk .  On my old hard disk I had Debian installed on a reiserfs partition.  My new hard drive is ext3.  When I boot into ubuntu it seems that some files are damaged in the reiserfs partition of my old hard drive.  When using "ls" in some directories it takes what seems like a whole minute before listing anything.  When it finally does list the directory contents some files are shown in bright red text color with a pitch black background.  Also using "ls -l" shows question marks for most of the fields.

I also noticed the 2 directories this happened in were mysql related.  One was /media/sdb3/var/lib/mysql/dbname and the other was /media/sdb3/home/me/.mysqlgui/query-browser

I think I may need to run fsck but not sure what options to use.  I'm also not sure what fsck can do and worried it could damage the files more somehow.

Thanks for any help!

---

### Post by jrusso2 on 2008-03-16
reiser has its own fsck, resierfsck.  I am not sure if this would cause damage or what the issue your having is however.

Did you try to resize the partition?

---

### Post by hotpockets on 2008-03-16
No, I didn't do any resizing on the install.  The install did reformat a swap partition on that disk though.  Also, the install gave me some weird error during the partition setup screen of the install.  The error had something to do with block sizes being twice the expected or something like that.  I chose the ignore option.  I believe that error was related to the NTFS partition though on that disk, so I don't think its related.

---

