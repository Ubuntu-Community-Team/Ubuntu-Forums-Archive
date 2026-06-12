---
title: "[SOLVED] About Permissions"
date: 2008-04-30
forum: General Help
---

### Post by rolodoom on 2008-04-30
```

drwxr--r-- 3 rolodoom rolodoom 4096 2008-04-30 20:16 fotos
drwxr-xr-x 2 rolodoom rolodoom 4096 2008-04-30 20:57 newfolder

```How do I make the 'fotos' folder to have the same permissions of 'newfolder' using terminal?

---

### Post by Dylnuge on 2008-04-30
You might want to read this:
[http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php](http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php)

Linux command is a great site for learning to use the terminal

Anyway, the command you are looking for is
```
 sudo chmod 755 fotos 
```

The syntax for that is:

```
 sudo chmod <mode> <file or directory> 
```

Mode is either a three digit number or a series of modification commands.

The number works as follows (the first is owner, second group, third everyone)
7-rwx
6-rw
5-rx
4-r
0-none

So 755 is rwxr_xr_x.

(R is read, W is Write, X is eXecute)

---

### Post by rolodoom on 2008-05-27
Excellent link about permissions. Thanks, really useful.

---

