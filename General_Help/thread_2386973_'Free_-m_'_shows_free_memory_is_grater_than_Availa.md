---
title: "'Free -m ' shows free memory is grater than Available Memory  on Ubutnu 16.04"
date: 2018-03-13
forum: General Help
---

### Post by pbodam on 2018-03-13
Please help me to understand the issue.

```
free -m
              total              used        free      shared  buff/cache   available
Mem:           3933        1152      1307          40        1473         519
Swap:          3903           6        3897
```

---

### Post by again? on 2018-03-13
[Understanding Linux memory usage]("https://andythemoron.com/blog/2017-04-23/Understanding-Linux-Memory-Usage")

---

### Post by coffeecat on 2018-03-13
Support, not chat.

*Thread moved to **General Help**.*

@pbodam, I've added BBCode code tags to your output from the terminal command free in an attempt to restore the proper formatting you would have seen in the terminal, but it looks as though you have may have added a bunch of spaces in an attempt at columnar formatting. If posting terminal output or code, please use code tags - see my sig for a link to how to do that - in order to preserve formatting. The forum software reduces multiple space characters to just one outside of code tags.

---

### Post by The Cog on 2018-03-13
**man free** gives a good explanation.

---

### Post by pbodam on 2018-03-15
Thank you for your replay , If you observe my output free is showing 1307MB  and available showing 519Mb . I have reviewed some blogs all the blogs says   free < available . but here free > available . i am want to understand why rest of 788MB is not being added in to available space. I want to know why it is behaving like this?

---

### Post by TheFu on 2018-03-21
[https://www.tldp.org/LDP/tlk/mm/memory.html](https://www.tldp.org/LDP/tlk/mm/memory.html)

Is the place to learn about memory management in Linux.  After that, I'd trust the manpages and the source code.

---

### Post by Yellow Pasque on 2018-03-21
[https://www.linuxatemyram.com/](https://www.linuxatemyram.com/)

---

### Post by TheFu on 2018-03-21
> **Temüjin said:**
> What would happen if your disk died right now?

I'd be slightly mad, since I put in a new SSD 2 weeks ago after a 3yr old SSD failed.  Of course, I restored from backup following my backup procedures, which have been well-tested before I considered them done.

Nice site link on memory.

---

