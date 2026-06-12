---
title: "What is /etc/cron.weekly/popularity-contest?"
date: 2007-08-26
forum: General Help
---

### Post by oldcpu on 2007-08-26
What is /etc/cron.weekly/popularity-contest?

This thing runs every week.  I did not do anything to join any popularity contest.  So why is it running in the background weekly?

---

### Post by heimo on 2007-08-26
> **oldcpu said:**
> What is /etc/cron.weekly/popularity-contest?

This thing runs every week.  I did not do anything to join any popularity contest.  So why is it running in the background weekly?

[http://packages.ubuntu.com/feisty/misc/popularity-contest](http://packages.ubuntu.com/feisty/misc/popularity-contest)
> 
 The popularity-contest package sets up a cron job that will periodically anonymously submit to the Ubuntu developers statistics about the most used Ubuntu packages on this system. 
 This information helps us making decisions such as which packages should go on the first CD. It also lets us improve future versions of Ubuntu so that the most popular packages are the ones which are installed automatically for new users.



What is the value of "PARTICIPATE" in /etc/popularity-contest.conf? Should be no by default, unless you give permission to send this information.

---

### Post by oldcpu on 2007-08-26
Thanks for the quick reply.  (And the link too.)

I am glad that it is disabled by default.  I thought I had spyware there for a moment.

---

### Post by heimo on 2007-08-26
> **oldcpu said:**
> Thanks for the quick reply.  (And the link too.)

I am glad that it is disabled by default.  I thought I had spyware there for a moment.

Yeah, your concern is understandable - I would be very irritated if I found out that my operating system had something like that enabled by default without my consent. But fortunately values / ethics of distribution like Ubuntu or Debian are very much against spying its users and privacy infringement. :-)

EDIT: Let's add that if one wants to enable this feature, in Gutsy Gibbon you go to System->Administration->Software Sources and then to Statistics tab and check Submit statistical information.

---

