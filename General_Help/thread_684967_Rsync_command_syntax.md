---
title: "Rsync command syntax"
date: 2008-02-01
forum: General Help
---

### Post by mistervino on 2008-02-01
I'm in need of a little rsync assistance...

Directory Contents:

```

-dir1
-dir2
-dir3
--subfile1
--subfile2
-file1
-file2

```

How can I use rsync (or another command) to copy the contents of this directory, but only subfile1 from dir3?  It should recursively disregard anything else in dir3.

 I can't seem to get the includes/excludes right.

Thanks!

---

### Post by weaverryan on 2008-02-01
This is the command that I run when using rsync

```

rsync --progress -azC --force --delete --exclude-from=config/rsync_exclude.txt -e "ssh -p22" ./ user@host:/path/to/destination/

```

You might need all that, but the key is that rsync_exclude file. My generally looks like this:

```
.svn
/dev/*
sync
.project
/logs/*
/public/assets/v1
/public/assets/admin
/public/uploads
config/application.php
```

It's all relative to the directory from which you're executing the command. This, for example, ignores all .svn files, everything in dev. the file sync etc. Modify for your use.

---

### Post by spupy on 2008-02-01
Do i understand you correct: you want to copy all dirs, but from dir3 - only subfile1? Or you want to copy only subfile1?

I'm sorry if i sound harsh, but you should check this out:
```
man rsync
```
What you need starts around line 2277 (wow :O)
Here are for example parts of my excludes/includes:
Exclude:
```
- Pics/
- Pics2/
- PROGRAMS/
- Video/
```
Include:
```
+ /Desktop/***
+ /Downloads/***
```
In this example it includes everything in "Downloads" except Pics, Programs, and Video.
I know it's very complicated, it took me awhile to get my lists correct by luck!

---

