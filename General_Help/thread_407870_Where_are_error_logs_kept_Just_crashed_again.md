---
title: "Where are error logs kept? Just crashed again"
date: 2007-04-12
forum: General Help
---

### Post by jhenager on 2007-04-12
I posted something a day or so ago about my hard disk dying, and it just did it again. I exited out of X-windows and saw a bunch of EXT3-fs error (device sda1) errors, but I can't locate the logs. I thought it would be in /var/logs.
I would like to get a printout of the crash so I don't get any static from the place where I bought the hard drive. Thanks.

---

### Post by rmemm on 2007-04-12
I assume you mean /var/log.  That's where I would look -- in one of those files.  I would look around a bit -- I never can remember which file -- there are so many logs.

Remember there is a normal log and a kernel log -- and the kernel log only sometimes get's posted to the normal log.  Both are in /var/log.  Maybe the kernel log is in dmesg but I can't remember.

Rob

---

