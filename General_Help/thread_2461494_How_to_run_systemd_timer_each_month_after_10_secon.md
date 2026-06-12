---
title: "How to run systemd timer each month after 10 second boot delay and not each day?"
date: 2021-05-01
forum: General Help
---

### Post by neeko37213 on 2021-05-01
Hello everyone! I'm fairly new to ubuntu and systemd. I would like to create a systemd service that would run each month and in addition after 10 seconds boot up process is completed. So, basically I would like that timer start service each month with a slight delay. I am aware that I one way I could achive this is by utilizing systemd timers, so I've tried following:

```
[Unit]
Description=run script monthly

[Timer]
OnCalendar=monthly
OnBootSec=5s
Persistent=true

[Install]
WantedBy=timers.target

```


```
[Unit]
Description=run script monthly

[Timer]
OnBootSec=5s
OnUnitActiveSec=1d

[Install]
WantedBy=timers.target
```

And still no luck, both cases fails, they execute service each time my pc reboots. For me seems like in the first case ignores "OnCalendar=monthly" and  instead executes my service each time I reboot my machine, and second  case likewise. In my understanding "OnUnitActiveSec=1d" would execute my  service and then remember last execution time, that way next execution  should be in next month but it executes after each reboot.

Also, my service file:
```
[Unit]
Description=run my script

[Service]
Type=oneshot
ExecStart=/usr/bin/myscript
 
```

How could I achieve that in systemd so my service is run each month with a delay? Is it even possible? Also I've tried putting ExecStartPre=/usr/bin/sleep 10 in the service file of unit to ensure delay, but that would hang my system for 10 seconds and won't let any user systemd unit run until sleep finishes.

 Thanks for reading, appreciate any help or advice

---

### Post by Xian on 2021-05-01
> **neeko37213 said:**
> 
```
[Unit]
Description=run script monthly

[Timer]
OnBootSec=5s
OnUnitActiveSec=1d

[Install]
WantedBy=timers.target
```

In my understanding "OnUnitActiveSec=1d" would execute my  service and then remember last execution time, that way next execution  should be in next month but it executes after each reboot.

The part missing in your description (shown in bold) is that 
> "OnUnitActiveSec=1d" **when paired with OnBootSec=5s** would execute my service **5 seconds after boot & again every day while the system is running** and then remember last execution time. 

So you are setting the timer to start at 5 seconds after boot and *again *each day while running. 
At each reboot the timer will restart just as you have instructed.

---

### Post by TheFu on 2021-05-02
I'd use cron.

---

