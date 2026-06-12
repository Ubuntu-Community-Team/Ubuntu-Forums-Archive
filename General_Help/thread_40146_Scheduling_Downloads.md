---
title: "Scheduling Downloads?"
date: 2005-06-07
forum: General Help
---

### Post by adwait on 2005-06-07
Hello everyone,

I am on an ADSL plan which limits my daytime downloads to 500 MB and I get unlimited downloads from 00:00 to 8:00. Is there a software which allows me do schedule the downloads so that they start at 00:00 and then pause (if they are not done yet) before 8:00?

Thanks,
Adwait

---

### Post by tread on 2005-06-07
Use cron to schedule a script, in which you setup the downloads using wget.

---

### Post by adwait on 2005-06-07
Can wget pause the downloads?

EDIT: OK I just RTFM and it does......

---

### Post by nocturn on 2005-06-08
Cron is for commands that run at regular intervals, so you can use it.
At does the one-time deal, just type:
```

at 00:01
>wget http://getithere/thefile
>CTRL-D

```

You can also use a download manager (requires you to stay logged in.  D4X integrates nicely with FireFox flashgot and is GTK2.

---

### Post by bored2k on 2005-06-08
There's a plugin for azureus that does this in case you use .torrents. BTW I'd go grazy with that ISP :-P

---

### Post by adwait on 2005-06-08
[QUOTE=bored2k]There's a plugin for azureus that does this in case you use .torrents. BTW I'd go grazy with that ISP :-P[/QUOTE]
 Hehe.....Well, I am getting a higher speed @ a cheaper rate so why not ;) I like trying different distros so need to download a lot too.......

Anybody can anyone tell me how do i setup a cron job? I tried typing cron at the root prompt but it says "cron: can't lock /var/run/crond.pid, otherpid may be 6612: Resource temporarily unavailable".

---

### Post by nocturn on 2005-06-08
> **adwait]Hehe.....Well, I am getting a higher speed @ a cheaper rate so why not  said:**
> 

I'll take your ISP any day ;-)  I'm on Cable and it is capped at 10 GB per rolling 30 days while only 2GB can be upstream.  It's even very expensive but there isn't a lot of competition here.

[quote]
Anybody can anyone tell me how do i setup a cron job? I tried typing cron at the root prompt but it says "cron: can't lock /var/run/crond.pid, otherpid may be 6612: Resource temporarily unavailable".

use the crontab command, cron launches the daemon.

---

### Post by 23meg on 2005-06-08
you might consider using d4x, which is a great gtk2 download manager. looks good and works like a charm; it's in the repositories.

---

### Post by adwait on 2005-06-08
[QUOTE=nocturn]I'll take your ISP any day ;-)  I'm on Cable and it is capped at 10 GB per rolling 30 days while only 2GB can be upstream.  It's even very expensive but there isn't a lot of competition here.



use the crontab command, cron launches the daemon.[/QUOTE]
 That's much much much more than my limit....when I said daytime downloads capped @ 500 MB, I meant 500 MB per MONTH not per day!! So that 500 MB is just good for surfing and maybe downloading a song or two........but the major downloading has to go on between 00:00 and 8:00. But its a flexible plan..so if I use more than 500 MB, i just have to pay more at the end of the month for each MB extra download.

---

### Post by adwait on 2005-06-08
:) thanks....exactly what I was looking for :)

---

