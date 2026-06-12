---
title: "is there any native linux fc.exe like program/script?"
date: 2008-06-06
forum: General Help
---

### Post by TheOne...more on 2008-06-06
hi,

i'm a windows user and i switched to linux four months ago. when i do archiving stuff, usually i check on the final disk and the original copies using fc.exe. now i know that some will say that linux has programs to compare files too, but there is something special about fc.exe. if you want to compare the contents of two directories without listing all the names of the files in them you would only type > c:\>fc /b dir1\* dir2\* and fc.exe will find the files with the same name and compare them. now this might seem as a rudimentary operation but it's so important because if i created a list of the directories in the original tree and saved it to the file tree.list for example, then typed > c:\>for /f "usebackq delims=|" %a in (".....\tree.list") do @fc /b tree1\%a\* tree2\%a\* i have both of the trees fully checked not only for binary consistency but also check whether there has been files that have their names changed due to file system differences, like between iso9660 and ntfs.

so does linux have a program or a script that does the job, i know i have to learn more bash and read more man pages but sometimes you need some Qsolutions, and any ideas are appreciated.

thanx

---

### Post by geirha on 2008-06-06
Read about the diff command by running ```
man diff
``` in a terminal. ```
diff -r dir1/ dir2/
``` might be what you want ...

---

### Post by TheOne...more on 2008-06-06
thanx geirha, it worked fine. i actually know about diff but i know it compares files as ascii rather than binary which keeps me wondering whether there is a program like diff but does it binary like fc.

the reason i'm asking is that in windows i encountered some two maybe three false inconsistencies because of using ascii mode rather than binary mode in comparison.

i actually don't know the difference, or the reason of inconsistency but thanx anyway, this is your 82nd thanx :)

---

### Post by geirha on 2008-06-06
It does check binary files as well. Consider the following example:
```

# Create two directories
$ mkdir dir1 dir2

# make a binary by compiling a simple c-program
$ echo -e '#include <stdio.h>\nmain(){printf("%f",12.34);}' | gcc -x c - -o dir1/file1

# copy the same binary to dir1/file2 and dir2/file2
$ cp dir1/file1 dir1/file2
$ cp dir1/file1 dir2/file2

# Make a slightly different binary for dir2/file1 (the float is slightly smaller):
$ echo -e '#include <stdio.h>\nmain(){printf("%f",12.12);}' | gcc -x c - -o dir2/file1

```
So now file2 are identical in each dir, while file1 differ slightly.
```

$ diff -r dir1 dir2
Binary files dir1/file1 and dir2/file1 differ

```

---

