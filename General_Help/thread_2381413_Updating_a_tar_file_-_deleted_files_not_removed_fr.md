---
title: "Updating a tar file - deleted files not removed from archive."
date: 2017-12-31
forum: General Help
---

### Post by meltingpot2015 on 2017-12-31
I create a tar file of the directory 'tartest'. This directory has the files: test1,test2, and test3:
> x@x:~$ ls -lh tartest
total 8.0K
-rw-rw-r-- 1 k k 18Nov  4 12:59 test1
-rw-rw-r-- 1 k k 57Nov  4 13:10 test2
-rw-rw-r-- 1 k k  0Dec 31 12:23 test3

I run: 
> x@x:~$ tar -cvpftest.tar tartest
tartest/
tartest/test2
tartest/test3
tartest/test1

list the files in the tar file:
> x@x:~$ tar -tvf test.tar
drwxrwxr-x k/k              0 2017-12-31 12:07 tartest/
-rw-rw-r-- k/k             57 2017-11-04 13:10 tartest/test2
-rw-rw-r-- k/k              0 2017-12-31 12:07 tartest/test3
-rw-rw-r-- k/k             18 2017-11-04 12:59 tartest/test1

Everything fine upto now!.

I then delete the file test3 from the directory 'tartest' then do:

> x@x:~$ tar -uvpf test.tar tartest
x@x:~$ List the contents of the tar file: 
> x@x:~$ tar -tvftest.tar
drwxrwxr-x k/k              0 2017-12-31 12:07 tartest/
-rw-rw-r-- k/k             57 2017-11-04 13:10 tartest/test2
-rw-rw-r-- k/k              0 2017-12-31 12:07 tartest/test3
-rw-rw-r-- k/k             18 2017-11-04 12:59 tartest/test1

'test3' is stillthere!. Shouldn't 'test3' have been removed from the archive when I ran
> x@x:~$ tar -uvpf test.tar tartest

How do I update the archive, so that deleted files are removed from the archive.:confused:

---

### Post by Holger_Gehrke on 2017-12-31
> **meltingpot2015 said:**
> Shouldn't 'test3' have been removed from the archive when I ran
```
x@x:~$ tar -uvpf test.tar tartest
```
How do I update the archive, so that deleted files are removed from the archive.:confused:

From the manual (man tar):
> -u, --update
              Append files which are newer than the corresponding copy in the archive.  Arguments have the same meaning as with -c and -r options.
tar (**t**ape **ar**chive) is primarily a backup program. Deleting a file from a backup just because it was deleted does not seem like a good idea. There is on option '--delete' for removing files from the archive, but since archiving and compressing are two separate tasks as far as tar is concerned (and compression is handled by another program that gets called by tar) this option does not work on compressed tar files.

Actually doing what you want is a bit more involved:
```

delfiles=$(tar -tf test.tar|while read fn ; do test -e "$fn" || echo $fn ; done); tar --delete -f test.tar $delfiles

```
This little script loops over the files in the archive and produces a list of all files that are in the archive but have been deleted at the source.The final command then deletes these files from the archive.
Holger

---

