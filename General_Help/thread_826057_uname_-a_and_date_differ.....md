---
title: "uname -a and date differ...."
date: 2008-06-11
forum: General Help
---

### Post by RichJacot on 2008-06-11
Hello,

I've been googling for a bit now and still haven't found an answer.

I realize that the date timezone comes from /etc/timezone, however....
Where does uname -a get its timezone from?

```
date
borg:~$ date
Wed Jun 11 14:01:15 CDT 2008
borg:~$ uname -a
Linux borg 2.6.24-18-rt #1 SMP PREEMPT RT Wed May 28 21:53:07 UTC 2008 x86_64 GNU/Linux

```

Notice date has CDT and uname has UTC, which is what I picked during install, but I'm trying to find where uname is pulling UTC from.

Thanks

---

### Post by hal8000 on 2008-06-11
I believe the date shown in uname -a is the date the kernel was compiled. Its always UTC, and if you compile your own kernel you will see the current date.

---

### Post by RichJacot on 2008-06-11
Ah.  Thank you!

---

