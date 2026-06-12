---
title: "System doesn't resume from suspend, shuts off instead with &quot;critical temperature&quot; msg"
date: 2021-01-03
forum: General Help
---

### Post by sigterm0 on 2021-01-03
Here's the log output of ```
sudo grep -Hrn 'critical temp' /var/log
```


```
/var/log/syslog:11407:Jan  3 11:19:54 Mirkwood kernel: [   42.487785] thermal thermal_zone4: critical temperature reached (128 C), shutting down
/var/log/syslog:16004:Jan  3 11:46:20 Mirkwood kernel: [  618.430389] thermal thermal_zone4: critical temperature reached (128 C), shutting down
/var/log/syslog:25429:Jan  3 11:53:26 Mirkwood kernel: [   58.861390] thermal thermal_zone4: critical temperature reached (128 C), shutting down
/var/log/syslog:30002:Jan  3 11:57:11 Mirkwood kernel: [   90.466069] thermal thermal_zone3: critical temperature reached (128 C), shutting down
/var/log/syslog:34442:Jan  3 11:58:56 Mirkwood kernel: [   58.555948] thermal thermal_zone4: critical temperature reached (128 C), shutting down
/var/log/syslog:38861:Jan  3 12:00:14 Mirkwood kernel: [   43.455529] thermal thermal_zone4: critical temperature reached (128 C), shutting down
/var/log/syslog:43280:Jan  3 12:01:37 Mirkwood kernel: [   37.089949] thermal thermal_zone4: critical temperature reached (128 C), shutting down
/var/log/syslog:47710:Jan  3 12:02:43 Mirkwood kernel: [   37.493875] thermal thermal_zone4: critical temperature reached (128 C), shutting down
/var/log/syslog:52164:Jan  3 12:04:15 Mirkwood kernel: [   44.518092] thermal thermal_zone4: critical temperature reached (128 C), shutting down
/var/log/syslog:56941:Jan  3 12:21:08 Mirkwood kernel: [  946.569103] thermal thermal_zone4: critical temperature reached (128 C), shutting down
/var/log/syslog:66055:Jan  3 14:06:41 Mirkwood kernel: [   69.711048] thermal thermal_zone4: critical temperature reached (128 C), shutting down

```


*All the entries are due to me suspending and trying to resume from suspend. System never went down by itself due to thermal issues. 


The thing is - It's happening only when trying to resume from suspend, even when laptop hasn't been used at all the last hour or so, I've been monitoring the temp using psensor and the temp never goes above 50 for any of the components so kinda clueless why this is happening. 


The system never shut off due to high temp and it's a brand new machine (bought during boxing day sale)

Laptop model is Lenovo X1 Extreme Generation 3
OS - Ubuntu 20.04

Any help is appreciated.

---

### Post by dino99 on 2021-01-04
Glance at errors (red lines) from 'journalctl -b' output into a terminal.

---

### Post by sigterm0 on 2021-01-04
> **dino99 said:**
> Glance at errors (red lines) from 'journalctl -b' output into a terminal.

I think it was due to upgrading the kernel to newest kernel. After downgraded to what Ubuntu 20 ships with the issue was resolved. However, I do not recommend anyone to install Linux on Lenovo X1 Extreme Gen 3 because the power doesn't even last 3 hours.

---

