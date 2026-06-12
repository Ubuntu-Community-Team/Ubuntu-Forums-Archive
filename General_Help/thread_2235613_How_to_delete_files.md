---
title: "How to delete files ?"
date: 2014-07-22
forum: General Help
---

### Post by sanko50 on 2014-07-22
I need a script to delete files which is 1 hr or older.  filename starts with virt*

rm -rf vir*  // this deletes all  files which starts with virt*

However I would like to delete such files which is 1 hr or older now.....what to write ?

Thanks

---

### Post by sudodus on 2014-07-22
You can use find with mtime, atime or ctime for long intervals and mmin, amin or cmin for short intervals. See ```
man find
```

```
find . -mmin +60 -type f -name "virt*"
```

and then develop the command with -exec for example

```
find . -mmin +60 -type f -name "virt*" -exec echo rm {} \;
```

and when you see that it is correct, remove the 'echo'

```
find . -mmin +60 -type f -name "virt*" -exec rm {} \;
```

and remove the files, when you know it is the correct selection.

---

### Post by sisco311 on 2014-07-22
The creation time of a file is not stored[SUP]*[/SUP], only the change time (ctime), modify time (mtime) and access time (atime). Please see [http://www.linux-faqs.info/general/difference-between-mtime-ctime-and-atime](http://www.linux-faqs.info/general/difference-between-mtime-ctime-and-atime)

Also on modern Linux systems, by default, the access time is only updated if the previous access time was earlier  than  the current modify or change time.

You can use the find utility to find files based on their atime, mtime or ctime. The GNU/find utility shipped with Ubuntu supports the -amin -cmin and -mmin tests. You can find the files which were modified more than an hour ago with:
```
find ./ -mmin +60 -type f
```

You can use the -name test to find file names which match a specific pattern:
 ```
find ./ -name 'virt*' -mmin +60 -type f
```

Please read [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind) for more details and examples about find.


[SUP]*) actually ext4 and other filesystems do have a file creation timestamp, but I'm not aware of a CLI utility which can access it.

EDIT: ninja'd by sudodus [/SUP]

---

