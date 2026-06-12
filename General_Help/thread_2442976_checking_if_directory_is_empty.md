---
title: "checking if directory is empty"
date: 2020-05-09
forum: General Help
---

### Post by Skaperen on 2020-05-09
i want to check if a directory is empty.  i am looking for a more efficient way.  i've tried 2 ways, so far. 1: list the files in it and count them.  if zero, it is empty.  2: if running as root or as the directory owner, try to _rmdir_ it.  if successful, it is empty.  then _mkdir_ it back (also, save and restore ownership dates, and mode)  this method has dangers.  both methods use more resources.  there may be reasons to check non-owned directors.

reading just the first two pages cannot determine this since there could be no files in them and maybe a file in one of thousands of subsequent pages.

i'm wondering which errors have priority.  for example, trying to _rmdir_ a directory that is open *and* non-empty.  do all POSIX systems give the same error (EBUSY or ENOTEMPTY/EEXIST)?

---

### Post by pqwoerituytrueiwoq on 2020-05-09
in a shell script i would do this
```
if [ $(ls -la /foo/bar|wc -l) -lt 3 ];then
  echo "folder empty"
fi
```
you could use rmdir and check the $? variable, but if it is empty do you want to delete it? you would also need write access
ls can take longer than rmdir especially if the list of contents is not in ram, unless you are doing this is a repeating loop it should not be issue

---

### Post by Skaperen on 2020-05-09
either way can be slow.  i'm just checking for a clever/innovative way to do it even faster.  i need to scan huge trees of 100000+ directories every day.  maybe i need to write something in C.

---

### Post by HermanAB on 2020-05-10
There are an infinite number of ways to do that:
[https://superuser.com/questions/352289/bash-scripting-test-for-empty-directory](https://superuser.com/questions/352289/bash-scripting-test-for-empty-directory)

---

### Post by Skaperen on 2020-05-10
18 is a little short of infinity (i consider the last 2 *rmdir* answers to be dups).  every solution with *ls* risks very slow performance with many very large directories.  *find* might be able to improve that but the question there was not about worst case performance and did not solve that.

what i would do in C is readdir() for one name and not read any more than that.  so if the directory has 1048576 files i only read a few (one page plus however many the system wants to pre-read).  it would be a limited amount of i/o (no o, just i).

---

### Post by Impavidus on 2020-05-11
Not every solution with ls risks slow performance with large directories. Don't pipe the output from ls -a into wc, but pipe it into a while loop reading one line at a time. If there are exactly two lines (. and ..), the directory is empty and you return 0. When you read a third line, return 1. This terminates the script and kills ls (with SIGPIPE?), so you don't waste time processing the other 9997 entries. I agree it's not very elegant. There must be a better way.

---

### Post by The Cog on 2020-05-11
How about:
```
find -type f -print -quit
```

---

### Post by Skaperen on 2020-05-11
that seems like it will work.  thanks!!

---

