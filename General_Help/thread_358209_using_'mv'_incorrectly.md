---
title: "using 'mv' incorrectly"
date: 2007-02-10
forum: General Help
---

### Post by pwrstick on 2007-02-10
I attempted to move a directory into another.  Both directories are on the same level.  So imagine this, wanting to move dir2 into dir1

/dir1
/dir2

to get

/dir1/dir2

I ran the following command:

mv dir2 /dir1

So in other words, I messed up the slash on the last one, and now the directory is gone.  I realize now I should have done:

mv dir2 dir1/

**But is there anyway of recovering the data?**  I can't find the dir2 anywhere...

---

### Post by ~LoKe on 2007-02-10
```
$ ls /dir1
```
Perhaps you moved it entirely.

---

### Post by Gibbs on 2007-02-10
I just tried it and lost my directory too.

---

### Post by Rab22 on 2007-02-10
What were the actual directory names?

There is a big difference between relative and absolute paths. So if the directories were "dir1" and "tmp" and you wanted to move "dir1" into "/home/username/tmp" and you did,

```
mv dir1 /tmp
```

as root, you'd get "/tmp/dir1" instead of "/home/username/tmp/dir1"

---

### Post by Gibbs on 2007-02-10
If you do mv dir2 /dir1 (or something similar) it will just rename dir2 to dir1.

It hasn't gone it's just been renamed (to dir1). To move it use mv dir2 ../

---

