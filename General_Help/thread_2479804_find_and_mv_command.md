---
title: "find and mv command"
date: 2022-10-08
forum: General Help
---

### Post by klapvogn on 2022-10-08
Hi,

I have some trouble finding out why this happens

```
find /path/to/source/ -name "*PATTERN*" -exec mv {} /path/to/dest/ \;
```

When i use the above line, it moves fine, but it leaves the folders behind it only takes the content and moves?

---

### Post by sudodus on 2022-10-08
Please

- create at test set of source and target directories with suitable content
- show an actual command line (that operates on the source and target directories)
- describe what happens and
- describe what you want to happen.

For example, do you want directory trees to be moved, or only files?

---

### Post by klapvogn on 2022-10-08
Hi,

I have tested some things, and when i use the above line it moves the files and NOT the folder+files. so it's here im stuck.

---

### Post by sudodus on 2022-10-08
Maybe the following structure and set of commands explains how to get what you want.

Please notice that

- moving a directory moves its whole directory tree (so you need not go deeper into its tree to move subdirectories and files there)
- moving files with the same name from different subdirectories to a single target directory will cause overwriting and loss of data.

If you move between different partitions, you should consider using **[FONT=Courier New]rsync[/FONT]** instead of find and mv (and delete from the source, when you know that the copying has finished correctly). **[FONT=Courier New]rsync[/FONT]** might be best also within a partition in order to decrease the risk of losing data.

```

$ find
.
./target
./file1
./source
./source/file1
./source/file2
./source/file3
./source/dir1
./source/dir1/file12
./source/dir1/file11
./source/dir1/file13
./source/dir2
./source/dir2/file21
./source/dir2/file23
./source/dir2/file22
./file2
./file3

$ find source/ -name "*file*" -exec echo mv {} target/ \;
mv source/file1 target/
mv source/file2 target/
mv source/file3 target/
mv source/dir1/file12 target/
mv source/dir1/file11 target/
mv source/dir1/file13 target/
mv source/dir2/file21 target/
mv source/dir2/file23 target/
mv source/dir2/file22 target/

$ find source/ -maxdepth 1 -name "*file*" -exec echo mv {} target/ \;
mv source/file1 target/
mv source/file2 target/
mv source/file3 target/

$ find source/ -maxdepth 1 -name "*1*" -exec echo mv {} target/ \;
mv source/file1 target/
mv source/dir1 target/

$ find source/ -maxdepth 1 -exec echo mv {} target/ \;
mv source/ target/
mv source/file1 target/
mv source/file2 target/
mv source/file3 target/
mv source/dir1 target/
mv source/dir2 target/
$ 

```

---

### Post by The Cog on 2022-10-08
It works for me. Without a concrete example from you, we can't tell what your problem is. 
Beware that it can confuse itself if the directory structure it is searching keeps changing. Try somethign like this - putting an echo command in there. Then you can see what it is going to do and maybe work out shere it's going wrong.
```
find /path/to/source/ -name "*PATTERN*" -exec echo mv {} /path/to/dest/ \;
```
You should put the {} in quotes to protect against filenames with spaces in them.

---

### Post by TheFu on 2022-10-08
> **klapvogn said:**
> Hi,

I have tested some things, and when i use the above line it moves the files and NOT the folder+files. so it's here im stuck.

If you want to move the directory and all objects it contains, then the PATTERN needs to be what you search and find.  I'd specify -type d to ensure only directories were found too.

BTW, replace the 'mv' with 'echo' to see what's being run by the 'exec' option.

---

