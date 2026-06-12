---
title: "Unreadable files - Unknown Type"
date: 2008-04-03
forum: General Help
---

### Post by 64mgb on 2008-04-03
I have a folder, which contains many files and subfolders, and suddenly they are all unreadable  and marked "Unknown type" in the file browser.  I believe this happened after I had to do a hard reset because the system was not responding.  Any idea what happened to them, and more importantly, how I can get them back?  I tried running GParted to scan and repair the filesystem, but it did not find any problems.

Thanks,
Rich

---

### Post by alan34 on 2008-04-04
in a terminal change to the directory before the one your are having problems with then try

sudo chown yourusername.yourusername yourfaultydirectory/

sudo chown -R yourusername.yourusername yourfaultydirectory/

The last two commands should give you ownership of the directory, subfolders and files.

then if you get desperate try

sudo chmod -R 777  yourfaultydirectory/

The above command gives everybody read, write execute permissions on the  directory, subfolders and files.

Good luck

---

### Post by 64mgb on 2008-04-04
Thanks, alan34 -

I actually figured that out a few miutes ago...after i did chmod on the top folder all is good.  But I appreciate you taking the time to post!

Thanks,
Rich

---

