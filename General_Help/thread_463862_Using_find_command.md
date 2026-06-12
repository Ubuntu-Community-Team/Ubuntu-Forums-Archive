---
title: "Using find command"
date: 2007-06-04
forum: General Help
---

### Post by carverj on 2007-06-04
Hi there everyone,
                                 The task for today is to use a find command to search the filesystem (/) for
all files ending with conf and to simultaneously display the number of lines in each of those files.
  My attempt was 
```
find / "conf$" | wc -l
```
But It doesn't seem to give the desired output.
Cheers in advance!!

---

### Post by moma on 2007-06-04
$ [COLOR="SeaGreen"]find / -name "*conf"  | wc -l [/COLOR]

This will output both file name and number of lines.
$ [COLOR="SeaGreen"]find / -name "*conf"  -exec wc -l {} \;[/COLOR]

---

### Post by Jussi Kukkonen on 2007-06-04
> **moma said:**
> $ [COLOR="SeaGreen"]find / -name "*conf"  | wc -l [/COLOR]

That'll actually only count the number of files. An alternative to your other suggestion is using xargs:
```
find / -name *conf | xargs wc -l
```
It's a bit more versatile as it works on any command, not just find.

---

### Post by moma on 2007-06-04
Kiitos Jussi.
You are right. The first example just counted the files not lines.

---

