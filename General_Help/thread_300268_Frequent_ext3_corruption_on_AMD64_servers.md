---
title: "Frequent ext3 corruption on AMD64 servers"
date: 2006-11-15
forum: General Help
---

### Post by jason_allen on 2006-11-15
We have 7 servers on dapper with 24/7 high loads (almost all disk based load). Some machines have software-raid, hardware-raid or no raid at all. Regardless, they all get corrupted file systems at a rate of about 1 server / 3 day (ie: mtbf for 1 server: 3 weeks). Fsck will usually restore the drives fine (but not always).

This is obviously untenable. Before doing something drastic (like moving away from Ubuntu), we are hoping the community here can help out with suggestions/ideas. We've tried upgrading to edgy (w/ 2.6.17 kernel) - but still experienced a failure. We ran the same hardware without a single glitch on breezy badger for 6 months - we highly suspect a kernel bug - but that's just a hunch.

Here are some details:
[LIST]
[*]All single or dual cpu opterons (each cpu is dual core)
[*]2/4/8GB ram
[*]All Western Digital drives (320GB sata II)
[*]mdadm raid, areca 1110, no raid ==> all have shown similar failures
[/LIST]

Btw - our next step is to move from ext3 to XFS since we came across some posts suggesting bugs with amd64, multi-proc & ext3. 

-jay

---

### Post by jason_allen on 2007-01-30
ok, for anyone stumbling on this topic. Here's what I know so far:

on AMD64 architectures with lots of ram (8GB here) - possibly dual proc (each dual core), with an areca 1110, we had endless corruptions - from kernel 2.6.15 on. Until we've recently updated to the latest feisty fawn release (kernel 2.6.20). Poof! No more corruptions - this is after 24 hours of stress testing. Hope this helps...

---

### Post by sourchier on 2007-02-09
This seems to be related to the corruption bugs described here: [http://pcburn.com/article.php?sid=2035](http://pcburn.com/article.php?sid=2035). It would be nice if you could provide us with some relevent information from /var/log/ from the servers. I hope that your servers are doing well with the feisty kernel. :guitar:

---

