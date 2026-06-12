---
title: "[SOLVED] Updating a tarball"
date: 2008-01-08
forum: General Help
---

### Post by PinkFloyd102489 on 2008-01-08
Im trying to use the -u switch to update a tarball in a script.

```
tar u Stuff.tar.bz2 Stuff/
```


That's the code I have now but it gives this error:

```
tar: Options `-Aru' are incompatible with `-f -'
Try `tar --help' or `tar --usage' for more information.
```



Any idea?

---

### Post by mali2297 on 2008-01-08
You cannot update compressed archives. A possible workaround is to uncompress the archive first, update it and then compress it again.
```

bunzip2 Stuff.tar.bz2
tar uf Stuff.tar Stuff/
bzip2 Stuff.tar

```

(The error that you got was about a missing f though.)

---

### Post by nowshining on 2008-01-08
open up the tarball with file-roller, go into the folder of the script u want to replace - and insert the new script - u won't be prompted to replace :/ itta auto replace it.

---

### Post by PinkFloyd102489 on 2008-01-08
I realized that I didnt actually want to update it. But thanks anyway. The tar is apart of an rsync script that Im making to add to crontab.


Thanks guys.

---

