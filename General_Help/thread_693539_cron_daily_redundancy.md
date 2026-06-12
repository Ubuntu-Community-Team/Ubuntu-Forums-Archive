---
title: "cron daily redundancy"
date: 2008-02-11
forum: General Help
---

### Post by undecidable on 2008-02-11
Key Point:

/etc/cron.daily has two daily jobs:
	find.notslocate
and
	slocate
both of which run updatedb. 

So in fact updatedb
will in fact be run twice.  

My guess is that the cron.daily job "find.notslocate"
is redundant and should be removed.  

Correct or rubbish?

-----------------
Some Detail:

I am guessing find.notslocate
is intended to run the old updatedb
which now seems to be called updatedb.notslocate. 

But in Ubuntu, I believe updatedb is simply a link to slocate that implies the -u (update) option,
and   find.notslocate is calling updatedb 
when I suspect it really wants to call updatedb.notslocate.

(I am aware they are both run ultimately by anacron not cron,
but that does not alter the question).
--------------

Using:  Feisty Fawn

---

