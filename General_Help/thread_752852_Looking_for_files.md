---
title: "Looking for files"
date: 2008-04-12
forum: General Help
---

### Post by breath2000 on 2008-04-12
My Lenovo 3000 notebook crashed and I am using ubuntu to recover lost files. I was able to see them with knoppix, but it wouldn't read my external hard drive. Now ubuntu can read my external drives but I can't see the files from the hard drive. Search did not find them. How can I find them?

---

### Post by geraldm on 2008-04-12
You can use the find command to search for the filename.  Use asterisk for grouping anything-at-all.  See the manpage for find.

find /mnt/topdirectory -name "myfil*" -print

you may need to prepend "sudo " to the command if there are permissions unavailable to you.

Gerald

---

