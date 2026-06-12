---
title: "test folder is empty shell script"
date: 2008-06-17
forum: General Help
---

### Post by dapim on 2008-06-17
hi,

how to check if folder is empty in shell script??

test -z only works for files, and for folder how i test it?

---

### Post by mike2357 on 2008-06-17
You could try this (assuming a directory name of my_dir) :

1.  ls my_dir/* > /dev/null 2>&1
2.  echo $?

Step 1 runs an "ls" of the directory contents and throws away the output.  However, a return value is still returned to the shell.

Step 2 checks the return value, and you could build this into your test command.  I think 0 means success, i.e. the directory had at least file or directory in it.  A return value of 2 means nothing found.

There's probably a more elegant way to do this, but this might do the trick.

---

### Post by kaibob on 2008-06-17
I use the following to do something similar:

```
filenumber=`ls | wc -l`

if [ $filenumber = 0 ]; then 
```

The filenumber variable returns both files and directories.

---

### Post by bodhi.zazen on 2008-06-17
if [ `ls dir | wc -l` -eq 0 ]; then

---

