---
title: "Shutting down via cron"
date: 2008-03-26
forum: General Help
---

### Post by mike-g on 2008-03-26
Hi,

What I want is for my PC to switch off at 5am. So I did:

sudo su -
crontab e

then in crontab...

0 5 * * *    /sbin/shutdown -h now

(saved that OK)

However this does not work (not shutting down). Can anyone help ?

also tried:

0 5 * * *    root /sbin/shutdown -h now


Thanks!

---

### Post by cmnorton on 2008-03-26
Shouldn't now be in quotes "now" ?

---

### Post by PinkFloyd102489 on 2008-03-26
You need to specify -hP instead of just -h. h means halt and P is power down.

Also, you dont need quotes.

---

### Post by mike-g on 2008-03-27
Thnaks for the replies - problem is the system is neither halting nor powering down (its still running and responding) - is there an error log that root 's cron jobs write to? This is driving me a bit crazy!

Thanks!

---

### Post by kpkeerthi on 2008-03-27
Look in /var/log

---

### Post by phrawzty on 2008-03-27
> **mike-g said:**
> Thnaks for the replies - problem is the system is neither halting nor powering down (its still running and responding)

Instead of shutdown, you may wish to try "poweroff"

```
$ which poweroff
/sbin/poweroff
```

As in :
```
0 5 * * * root /sbin/poweroff
```

It's a symlink to "reboot", which is, in turn, a binary that works with both runlevels and power states.  Plus it's easier to remember "poweroff" as a command. ;)

---

