---
title: "Files manager shows no files but ls lists many"
date: 2024-07-05
forum: General Help
---

### Post by klundermann on 2024-07-05
I'm running 22.04.

According to the [FONT=system]Files [/FONT]graphical file manager, the [FONT=system]BACKUP[/FONT] directory on my external HDD is completely empty (1st attachment).

According to  [FONT=system]ls -a[/FONT]  it's got lots of files, some of which, weirdly, cannot be listed, because they not exist (2nd attachment, showing the last few dozen of output).

When I try to delete any of the files, I get a "No such file or directory" error.

Which, if either, is correct? How do I get them both to be correct?

---

### Post by currentshaft on 2024-07-05
What do these commands return in that directory?

pwd
mount | grep $(pwd)
lsblk
file *

---

### Post by klundermann on 2024-07-07
The output of [FONT=system]**pwd**[FONT=arial] is ```
/media/<*username*>/LaCie/BACKUP
```**(LaCie** is the name of the HDD).

[/FONT][/FONT]**mount | grep $(pwd)** returns nothing.

**lsblk** returns many lines; I presume the relevant ones are the last 2:
```
sdc      8:32    0 298.1G  0  disk
'-sdc1   8:33    0 298.1G  0  part  /media/<*username*>/LaCie
```

The output of **file *** is much the same as that of **ls:** dozens of lines of complaints of the form:
```
 duplicity-inc-.2024.<...>.gpg: cannot open `duplicity-inc-.2024<...>.gpg' (No such file or directory)
```

---

