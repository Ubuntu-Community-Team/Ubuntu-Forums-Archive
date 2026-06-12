---
title: "Starting firefox too soon makes everything grind to a halt"
date: 2007-06-20
forum: General Help
---

### Post by dignick on 2007-06-20
I've added kopete to my startup programs in Ubuntu 7.04, and it takes a while to start.  That's no problem in itself, I can wait.  But if I start firefox before kopete has started properly, kopete does not load or may load at some point in the distant future, and firefox and in fact the whole system is unbearably slow.  I have no idea why this happens, and so I just restart the computer every time I mistakenly start firefox too early as restarting firefox or killing kopete and related processes doesn't fix it. As you can imagine, this is quite frustrating.
I think the same thing happened when I used pidgin instead of kopete, but it started a lot quicker so it was less noticable.
Any suggestions on how I could fix this?
Thanks.

---

### Post by Kubunteando on 2007-06-20
Can you check/post the output of the "top" command when that is happening?

Do you have enough memory? 
How about swap memory (you can check with "swapon -s")?

---

### Post by dignick on 2007-06-22
> **Kubunteando said:**
> Can you check/post the output of the "top" command when that is happening?

You know, this is one of those things where it only happens when you don't want it to.  I'll post it when it happens again, but for the first time ever it didn't occur when I started firefox.

> Do you have enough memory? 
How about swap memory (you can check with "swapon -s")?
Output of that command:
```
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       498004  11768   -1

```
I have 1024mb of real memory.

---

