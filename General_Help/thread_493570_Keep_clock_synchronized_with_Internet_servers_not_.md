---
title: "Keep clock synchronized with Internet servers not working"
date: 2007-07-05
forum: General Help
---

### Post by spiderworm on 2007-07-05
Hi,

On a Dapper machine there seems to be a problem where the time starts running ahead a couple minutes every few weeks or so.  I know about the "Keep clock synchronized with Internet servers" option; trouble is, it doesn't seem to work.  I have the necessary ntp packages installed and I have selected a time zone and servers to sync with; nonetheless, the clock still runs fast and I have to come in every couple of weeks to deselect the "Keep clock synchronized with Internet servers" and press the "Synchronize now" button or whatever.  It's really quite annoying, especially because this box happens to be a MythTV box and it starts cutting off more and more of each show every couple of days.

Does anyone know what cron process and scripts are supposed to be run iwth the "Keep clock synchronized" option?  I think I can figure out what the problem is from there.

Thanks,
David

---

### Post by NeoLithium on 2007-07-05
Have you installed the network time protocol?  If not, try this:
```

sudo aptitude install ntp

```
Then try again, and it should allow you to select which servers you want to use to synchronize the clock with.

---

### Post by spiderworm on 2007-07-05
> **NeoLithium said:**
> Have you installed the network time protocol?  If not, try this:
```

sudo aptitude install ntp

```
Then try again, and it should allow you to select which servers you want to use to synchronize the clock with.

Already installed.  If you re-read my post, you'll see that I have already installed the packages and I was able to select what servers and and sync with the servers but cannot get it to automate the process.

Please let me know if some part of my post was not clear.

Thank you,
David

---

