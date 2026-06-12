---
title: "folder exclusion using the find command"
date: 2008-04-16
forum: General Help
---

### Post by whitegourd on 2008-04-16
I'm trying to set exclusions within the find command.  In particular exclude a directory and everything below it.  In my example, I seem to be able to exclude the "three" directory, but yet cpio still archives the three text files within it.  Can someone assist me in how to do this correctly?  Thanks.

```
root@server:~/test# find . -depth \
> -not -name "three" \
> -not -name "bkup.cpio" \
> -print | cpio -o > bkup.cpio
2 blocks
root@server:~/test# cpio -tf < bkup.cpio
three/2.txt
three/1.txt
three/3.txt
two/2.txt
two/1.txt
two/3.txt
two
one/2.txt
one/1.txt
one/3.txt
one
.
2 blocks
root@server:~/test#
```

---

### Post by Brucevdk on 2008-04-17
How about: 
```
find . \( -name "three" -o -name "bkup.cpio" \) -prune -o -print
```

Thanks to: [SUMMARY: Find to exclude dirs/subdirs](http://www.sunmanagers.org/pipermail/summaries/2004-April/005199.html).

---

### Post by whitegourd on 2008-04-18
That worked.  Thanks!

---

