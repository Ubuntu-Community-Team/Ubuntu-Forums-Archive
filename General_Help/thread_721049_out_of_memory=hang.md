---
title: "out of memory=hang?"
date: 2008-03-10
forum: General Help
---

### Post by leptogenesis on 2008-03-10
I was following the directions on this website:

[http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html](http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html)

The website contains programs which use up all the system's memory.  I compiled the first program, ran it, and it died, just as expected.  Then I did the same for the second program.  But in that case, it ran fine for the first 1000 megabytes, it started swapping for the next 500 megabytes, and then the whole system locked up.  And I mean the whole system--not even the mouse would move.  Anyone know why this is happening?  Is there some setting which makes Linux kill programs that use too much memory, which got turned off in my system?  

I'm running xubuntu on a Dell Inspiron e1505 with 2 gigs of ram.  /proc/version says:

Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008

---

### Post by Vadi on 2008-03-11
All OS's will have this behavior when running out of memory (for example, you can lock up any vista in under 20 seconds by holding down Windows key + E).

I wouldn't be suprised if there was some setting you could do to not allow a program take up more than % of your max ram or something though.

---

### Post by leptogenesis on 2008-03-11
> **Vadi said:**
> All OS's will have this behavior when running out of memory (for example, you can lock up any vista in under 20 seconds by holding down Windows key + E).

lol...I need to try that...

However, according to the site, Linux is supposed to avoid this problem by killing any application that requests more memory than is available on the system.  This is especially important on a many-user system; such a system shouldn't go down if one person goofs up.

> **Vadi said:**
> I wouldn't be suprised if there was some setting you could do to not allow a program take up more than % of your max ram or something though.

I think ulimit does something like that...I guess that might solve the problem, although it's quite painful to explicitly set limits for every user...

Anyway, thanks for the response Vadi.  Can anyone else reproduce the problem?

---

