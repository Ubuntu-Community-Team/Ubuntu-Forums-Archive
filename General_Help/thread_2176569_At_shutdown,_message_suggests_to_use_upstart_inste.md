---
title: "At shutdown, message suggests to use upstart instead of old /etc/init.d/"
date: 2013-09-25
forum: General Help
---

### Post by wolterh on 2013-09-25
Every time I shutdown, I get the purple console where all messages are print out, and among those I read
> 
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service networking stop.
Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the service(8) utility, e.g. service networking stop.


I would delightfuly use upstart instead of the /etc/init.d interface, but I can't see how to fix this.

---

