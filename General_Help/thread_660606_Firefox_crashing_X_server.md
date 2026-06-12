---
title: "Firefox crashing X server"
date: 2008-01-06
forum: General Help
---

### Post by dicer99 on 2008-01-06
I am using Ubuntu 7.10. I have had various problems with Firefox in the past. Sometimes it stops responding and I usually fix this from an xterm with:

```
"pkill firefox-bin"
```

However, recently, rather than firefox simply freezing; it is now crashing the whole X server and returning me to the GDM login screen.

I did not have the problem with X crashing when I first starting using 7.10. It is more recent. I believe that it has been triggered by a recent update. When I say recent, I mean probably within the past 50 days; as I had about 50 days uptime and the problem began after re-starting a few days ago.

I have checked /var/log/syslog and found the following:

```
Jan  7 04:35:01 localhost gdm[15532]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
```

I am currently using kernel 2.6.22-14. I just re-started a few days ago, so this is the main difference to the system.
I am running Firefox 2.0.0.11

---

