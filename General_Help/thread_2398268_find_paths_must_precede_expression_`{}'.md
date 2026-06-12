---
title: "find: paths must precede expression: `{}'"
date: 2018-08-09
forum: General Help
---

### Post by raleigh3 on 2018-08-09
```
andy7_/media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04$ find '/media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/'* -mtime +5 {} \;
```

---

### Post by TheFu on 2018-08-09
Try```

$ find /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/ -mtime +5 -print
```
with or without the trailing / on the directory.  But if this is a mounted distro CD image from April, all the files should be found.

If your CWD is that directory, you can just specify . instead.
```

$ find  .   -mtime +5 -print
```

Interactively, using . is easier or any relative path.
For scripts, using the fully-spelled-out path is the best practice.

find is one of the commands where seeing lots of examples is very,very helpful.  There are a number of blogs/websites with 20+ examples.  There's also a website that will explain almost every Unix command + options. [https://explainshell.com/](https://explainshell.com/)

---

### Post by raleigh3 on 2018-08-10
Thanks for the link.

See my post for "Delete 3 oldest files."
[h=2][/h]

---

