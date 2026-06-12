---
title: "schedule a shutdown"
date: 2007-06-03
forum: General Help
---

### Post by oliv66 on 2007-06-03
Hello everyone,

WHen I need to schedule a shutdown in x  days, I can use Gshutdown if I am under Gnome.

In a terminal, I can use shutdown + make a calculation of the number of minutes to have the equivalent of  a few days

Is there any way to use a given  date ?  I am pretty sure to have done it in the past but I cannot remember the right syntax after trying many date formats.

Help welcome.

Thanks in advance,

---

### Post by yabbadabbadont on 2007-06-03
You could schedule an ad-hoc cron job using the "at" command.  I would have to check the manpage, but I'm fairly certain that you could do something like:

at 12:31PM 12/23/07 command to be run here

---

### Post by oliv66 on 2007-06-06
Thanks,

I was dead-convinced there was another way than using a cron job.

---

### Post by steeleyuk on 2007-06-06
at the terminal type:

shutdown --help

it will give you a list of shutdown commands. one includes specifiying a time. don't know of any GUI which enables this (there most likely is one) but its not a feature i've ever used...

Edit: sorry, I see you already know how to do that (note to self: read post fully first)

---

