---
title: "glxgears"
date: 2007-01-15
forum: General Help
---

### Post by allwin on 2007-01-15
When I run glxgears, I see the gears moving but...it doesn't print out any frame rates.  I run it from TERMINAL.  OK, maybe there is some trick command here.  I tried searching on GLXGEARS in Google but too many hits, and even the man pages say it's going to print framerate information...but it doesn't.  What could I be doing wrong here?  I finally got Beryl working and so on and I wanted to explore what the performance was on my old test system, just out of curiosity.

---

### Post by pay on 2007-01-15
```
glxgears -printfps
```

---

### Post by ~LoKe on 2007-01-15
When did this change, and is there a reason?

Some people get a printout without using the arguments, is that only on older distributions (Dapper, Breezy, Hoary)?

---

### Post by fragos on 2007-01-15
I noticed the change after upgrading from 6.06 to 6.10 but I hadn't run glxgears in a while.  Only the developer would lnow why they did it?  Since they had to write code they must have had a reason.  As a benefactor of free software created by someone that doesn't get paid, I accept changes and adapt to them.  If I want something different, I'll write myself.

---

### Post by ardchoille42 on 2007-01-16
Just to let you know, I am using Ubuntu 6.06.1 LTS (Dapper) and the command

```

glxgears -printfps

```

Runs glxgears and prints out the fps in the terminal.

---

### Post by cjazz on 2007-01-16
As for the reason for the change, I think there may be a clue in the alternate command:

 glxgears -iacknowledgethatthistoolisnotabenchmark

which also prints out framrates.

---

