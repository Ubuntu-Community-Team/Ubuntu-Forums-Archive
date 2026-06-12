---
title: "Watchdog service not getting started by default"
date: 2015-08-28
forum: General Help
---

### Post by moon-linux on 2015-08-28
Hi All,

I am using Ubuntu 15.04 Mate.

I have installed watchdog and configured watchdog demon by modifying /etc/watchdog.conf and /etc/default/watchdog configuration files.
watchdog module is getting loaded when configured.

But these service seen not able to run by default.

I want watchdog service to start on every boot.

Please some body could give me pointers.

-Anand Moon

---

### Post by sandyd on 2015-08-28
Hi, Ubuntu 15.04 now uses systemd to manage startup.

Watchdog may not have the right config.

Can you post the output of
```

systemctl list-unit-files --type=service

```

You may have to hold down enter until it reaches the end of the output.

---

