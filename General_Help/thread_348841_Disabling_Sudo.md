---
title: "Disabling Sudo"
date: 2007-01-29
forum: General Help
---

### Post by thomasaaron on 2007-01-29
Hi, folks.

I need to be able to occasionally run a shell script, certain parts of which require sudo priveleges, without me having to be there to enter my password. In other words, it MUST be completely automatic.

While I know a lot of you will bristle at this question... Is there a way to temporarily disable the password protection (sudo) so that the script no longer requires superuser priveleges? 

Or, how can I automate the detection and entry of my password when the script requests a prompt?

Or, is there some other workaround?

Best,
Tom

---

### Post by taurus on 2007-01-29
The best way to go about it is to add that username and the name of the program in /etc/sudoers.  Then, it will not ask for any input if that user runs that program.

```
man sudoers
```

---

### Post by bscbrit on 2007-01-29
If the script must run at a set time interval, simply place it in your cron job list.  It will be invoked automatically by the system and will run with root privs.  Many administrative tasks already run this way.

---

### Post by thomasaaron on 2007-01-29
Excellent.
Thank you both.
Best,
TOm

---

