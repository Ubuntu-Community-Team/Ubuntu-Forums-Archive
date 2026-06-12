---
title: "Time sync problems - Winter clock."
date: 2006-10-29
forum: General Help
---

### Post by finalbeta on 2006-10-29
Time changed to winter hour today. I figured my Ubuntu install would change the time for me, but no such luck.

I went to the time and date dialog, pressed the "Synchronise now" button, nothing happened.

So I installed nntp to keep the clock synchronized. Nothing happened. I then manually had to open the select server dialog and close it before it did anything. pretty stupid since the default Ubuntu server is selected anyway.

Anyway, ignoring the fact that there is lots of work to be done before we get proper GUI configuration, can someone confirm this issue of Ubuntu not adjusting to winter clock and the "Syncronise now" button that fails to work?

//edit , I'm using Edgy and one of my machines did adjust time, one didn't.

---

### Post by ronmarley1 on 2006-10-29
When I booted up today, my clock was automatically adjusted back to EST from DST.  I'm using Dapper.

---

### Post by bihe on 2006-10-29
I also have an issue concerning the change from CEST to CET today. 
Successfully synchronized and updated the computer time, but now i have some strange sudo features:

```
[henrik@aragorn ~]# sudo -s
sudo: timestamp too far in the future: Oct 29 19:00:43 2006
```

my system time:

```
[henrik@aragorn ~]# date
Sun Oct 29 18:14:23 CET 2006
```

---

### Post by comppsyco on 2006-10-29
Same problem here. Please help!

---

### Post by yabbadabbadont on 2006-10-29
Wait an hour and it should be fine.

---

### Post by finalbeta on 2006-10-29
> **yabbadabbadont said:**
> Wait an hour and it should be fine.

My desktop was running the whole day.

---

### Post by yabbadabbadont on 2006-10-29
> **finalbeta said:**
> My desktop was running the whole day.

Sorry, my post was for post numbers 3 and 4.

---

### Post by bihe on 2006-10-30
Yes, just a temp feature!

---

