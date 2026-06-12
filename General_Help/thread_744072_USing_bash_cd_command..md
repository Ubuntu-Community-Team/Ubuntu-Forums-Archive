---
title: "USing bash cd command."
date: 2008-04-03
forum: General Help
---

### Post by Zophixan on 2008-04-03
Hey guys, how would I use the cd command to move to say:
system:/media/sdb1/games/DeusEx/System

when I type cd system:/media/sdb1/games/DeusEx/System , it claims it can't find the path, the path in question is on an external hardisk..Come to think of it, I haven't been able to use any paths with the CD command, except for moving into a dictionary, then moving into a nother etc.

---

### Post by jrib on 2008-04-03
You want ```
cd /media/sdb1/games/DeusEx/System
```

/ is the root of your filesystem.  Everything branches from there.

Here's a nice guide for using the terminal (with more nice guides as references at the end too):
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

