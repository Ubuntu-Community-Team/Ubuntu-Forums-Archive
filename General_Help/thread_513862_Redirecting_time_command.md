---
title: "Redirecting time command"
date: 2007-07-31
forum: General Help
---

### Post by DBQ on 2007-07-31
Hi Everybody,
    Sorry if this sounds dumb.  But I am writing a shell script, and I need to redirect the output of the time command to a file.  For example: 

time ls >> file

Right now it only outputs to a terminal no matter what I do.

---

### Post by PaulFr on 2007-07-31
```
 ( time <command> ) > file1 2> file2
``` will put the output of the <command> in file1 and the output of the **time** command in file2. Of course, you can use **2>>** to append instead of overwrite.

---

### Post by DBQ on 2007-07-31
Seemed to work.  Thanks for the hint.

---

