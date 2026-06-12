---
title: "crontab help"
date: 2008-03-31
forum: General Help
---

### Post by I.You on 2008-03-31
Hello guys

I'd like to know if there's any way to run one first and the other (about 1 min.) later as two tasks are set as same time in cron table.
is it possible?

Please let me know the site or docomentations about it.

Thanks.

---

### Post by justleen on 2008-03-31
so, you have two tasks, set at the same time in cron, but you want to have run not at the same time, but 1 minute after each other?

just change the time it runs in cron?

---

### Post by I.You on 2008-03-31
Yes, because something will be wrong if 2 tasks run at the same time.
so I want to run one first and then the other later.
I want to know if it is possible to do so in cron table because the modification of a program that sets the time in cron table is too complicated.

Thanks for reply.

---

### Post by chilinski on 2008-03-31
Does the first task have to be completed before the second one runs? What if the first task is still running when the second one starts? Is that a problem?

This is probably not a job for cron but for a script. I'm sure people here with hardcore scripting could help you out better than I. 

Here's a really simple approach. Write a script that contains something like this:

Run the first task
sleep 300 #just hang out for 5 minutes
Run the second task

Make this file executable and call it in crontab.

---

