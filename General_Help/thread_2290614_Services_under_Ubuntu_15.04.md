---
title: "Services under Ubuntu 15.04"
date: 2015-08-13
forum: General Help
---

### Post by JP_Wallhorn on 2015-08-13
Hi guys,


I just upgraded my server from Ubuntu 14.04 to 15.04 and something must have changed how the services work now because I get weird error messages.

I just installed a tool called 'Supervisor'. When I want to use the statement ```
service supervisor restart
``` I get the following error msg ```
Job for supervisor.service failed. See "systemctl status supervisor.service" and "journalctl -xe" for details.
```

I'm not an expert and I'm trying to find a solution here but nothing has helped so far. I hope you can clarify what exactly has changed and how I can fix this.

Btw. when I use ```
systemctl restart supervisor
``` I get the same msg.

---

### Post by bab1 on 2015-08-13
> **JP_Wallhorn said:**
> Hi guys,


I just upgraded my server from Ubuntu 14.04 to 15.04 and something must have changed how the services work now because I get weird error messages.

I just installed a tool called 'Supervisor'. When I want to use the statement ```
service supervisor restart
``` I get the following error msg ```
Job for supervisor.service failed. See "systemctl status supervisor.service" and "journalctl -xe" for details.
```

I'm not an expert and I'm trying to find a solution here but nothing has helped so far. I hope you can clarify what exactly has changed and how I can fix this.

Btw. when I use ```
systemctl restart supervisor
``` I get the same msg.
It did change.  You are now using systemd instead of upstart.  I haven't updated yet so I don't know any of the specifics.  I would do just as the error message said to do; try this command```
systemctl status supervisor.service
```...judging by the structure and the little I have read, I think this might start your app```
systemctl restart supervisor.service
```

Let's us know if this works.

---

### Post by JP_Wallhorn on 2015-08-13
Same error message

---

