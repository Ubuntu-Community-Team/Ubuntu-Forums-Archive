---
title: "how can i get a text file containing the filenames of all files in a folder?"
date: 2016-04-12
forum: General Help
---

### Post by triciasurfer on 2016-04-12
i have a bunch of files in a folder. is there a quick way to get a list of their filenames into a simple text file? just one filename per row.

---

### Post by howefield on 2016-04-12
There are a load of ways, a simple ls would probably do it.

```
ls /path/to/source/ > filelist.txt
```

Is it a single folder or are there subfolders to be listed also ?

---

### Post by vasa1 on 2016-04-12
...Deleted because what I posted doesn't take into account filenames with spaces and characters that may cause issues.

---

### Post by sisco311 on 2016-04-12
In Linux, a file name can contain any character except a slash (`/') and the null character (`\0'). The slash is the name of the root directory and it's also used as a path separator and the null character is used as the path terminator.

The only problem with `ls' is that it doesn't print the actual file names. It prints a human readable representation of the filenames.

---

### Post by Impavidus on 2016-04-12
Printing the filenames one name at each line may be impossible as filenames may contain newline chracters, but in practice this rarely happens. If it applies to you, you can use **ls -b**, which will replace the nongraphical characters by escape sequences. In most cases howefield's solution will be enough.

---

### Post by vasa1 on 2016-04-12
> **sisco311 said:**
> In Linux, a file name can contain any character except a slash (`/') and the null character (`\0'). The slash is the name of the root directory and it's also used as a path separator and the null character is used as the path terminator.

The only problem with `ls' is that it doesn't print the actual file names. It prints a human readable representation of the filenames.

Thanks for the reminder. **find** may be more suitable. I try to keep my filenames clean of characters that may cause confusion.
```
find ~ -type f
```prints filenames in one's home folder on single lines but the path is included. 
```
find . -maxdepth 1 -type f
```will do the same in the current folder. The default is recursion but then **maxdepth** may be useful to control how deep one goes.

Edit: OP maybe interested in [detox]("http://linux.die.net/man/1/detox"): "utility to replace problematic characters in filenames"

---

