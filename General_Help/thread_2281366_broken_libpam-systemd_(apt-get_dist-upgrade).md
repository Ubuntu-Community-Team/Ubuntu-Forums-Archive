---
title: "broken libpam-systemd (apt-get dist-upgrade)"
date: 2015-06-06
forum: General Help
---

### Post by a_m on 2015-06-06
Hallo, 
it seems that an "apt-get update/upgrade/dist-upgrade" broke something on my Ubuntu Mate 14.04 Installation.


start: Job failed to start
invoke-rc.d: initscript systemd-logind, action "start" failed.
dpkg: error processing package libpam-systemd:amd64 (--configure):
Errors were encountered while processing:
 libpam-systemd:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any idea of how to fix this?
Thanks!

---

### Post by Bashing-om on 2015-06-06
a_m; Humm ..

Might be as simple as (RE-)installing ? Sure worth a shot and see what results:
```

sudo apt-get install --reinstall libpam-systemd

```

[INDENT][INDENT]possible, that it could happen\
[/INDENT][/INDENT]

---

