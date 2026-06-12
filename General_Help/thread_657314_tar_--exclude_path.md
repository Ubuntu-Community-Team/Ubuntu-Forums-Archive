---
title: "tar --exclude path???"
date: 2008-01-03
forum: General Help
---

### Post by danifodor on 2008-01-03
Hi!

I am trying to tar a directory (for backup) but I cannot exclude the path.
From: /home/user/something1
To: /server/user/something2

After 
```

tar cvf /server/user/something2/backup.tar.gz /server/user/something1

```
you can see the path in backup. I tried to tar with the --exclude='the_path' but it did not work. I made a small script:
```

#! /bin/sh
cd /home/user/something1
tar czf /server/user/something2/backup.tar.gz ./*
exit 0 

```
but I am curious whether it is possible to solve the problem in one single row (without --exclude may be?)

Cheers 

Daniel

---

### Post by geraldm on 2008-01-03
Where the path is /usr/EXCLUDE_THIS/dosave/file1
```

tar -cvf backup.tar -C /usr/EXCLUDE_THIS dosave

```
The path /usr/EXCLUDE_THIS will not appear in the pathname of the saved file(s)

check man tar for the -C option

Gerald

---

