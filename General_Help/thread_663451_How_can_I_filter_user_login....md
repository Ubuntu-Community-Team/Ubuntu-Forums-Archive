---
title: "How can I filter user login... ?"
date: 2008-01-10
forum: General Help
---

### Post by ubuscout on 2008-01-10
Hi to everybody,

I need to filter the access of my soons to the desktop... I would like let them to access at my ubuntu desktop only in the evening (ie 19.00 to 21.00) ...

Is it possible ? ...which is the best way (in system>administration/preference  I didn't see something could help me isn't it...)   ??!

thx

---

### Post by ubuscout on 2008-01-10
Nobody could help me ?!  ...I really need, setup this control access... plz

thx

---

### Post by bodhi.zazen on 2008-01-10
You might check out timeoutd :

[http://www.penguin-soft.com/penguin/man/5/timeouts.html](http://www.penguin-soft.com/penguin/man/5/timeouts.html)


[http://www.digipedia.pl/man/timeoutd.8.html](http://www.digipedia.pl/man/timeoutd.8.html)

[http://man.cx/timeouts(5](http://man.cx/timeouts(5))

From the third link :

> Wk2000-0700:ttyS*:*:*:NOLOGIN
              Would match all dialled in users (if all ttyS lines were modems)
              and prevent them logging in before 7am or after 8pm on weekdays.

You may need to play with it a little ;)

---

### Post by ubuscout on 2008-01-11
> **bodhi.zazen said:**
> You might check out timeoutd :

[http://www.penguin-soft.com/penguin/man/5/timeouts.html](http://www.penguin-soft.com/penguin/man/5/timeouts.html)


[http://www.digipedia.pl/man/timeoutd.8.html](http://www.digipedia.pl/man/timeoutd.8.html)

[http://man.cx/timeouts(5](http://man.cx/timeouts(5))

From the third link :



You may need to play with it a little ;)


thx for the help...  it seem exactly what I need :), so I've tried it, but ... 

...it doesn't work.... :(

I have insert these line in /etc/timeouts

Wk2101-1859:*:sara:*:NOLOGIN
Wk1900-2100:*:sara:*:*:30:30

from my account I've checked with 'ps aux' timeoutd is up :

root      5307  0.0  0.0   2736   500 ?        Ss   18:25   0:00 /usr/sbin/timeoutd

but If now I switch in user "sara"  I can make login without problem... have notice when I've tried was 18.15 for example...

Now... I ask me, maybe  timeoutd doesn't  work graphic login (gdm) ?!?  :confused:


...here I am again... :(

---

### Post by ubuscout on 2008-01-11
...tried login also in terminal console, and it doesn't work... :(

---

### Post by ubuscout on 2008-01-11
...sorry, I've writed above too much quickly...  by terminal seem it works... but by graphic login it doesn't work...

---

