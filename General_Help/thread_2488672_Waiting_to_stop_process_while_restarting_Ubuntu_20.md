---
title: "Waiting to stop process while restarting Ubuntu 20.04 LTS"
date: 2023-07-12
forum: General Help
---

### Post by ommiorih on 2023-07-12
Hi,
got Ubuntu 20.04 LTS, sometimes when I start system I want to restart it immediately after it started. I'm often facing huge delay in restart, because there is "stopping process delay" which might take 90 seconds. How do I reduce that time to lower value like 5 seconds?

---

### Post by gcvl on 2023-07-12
Try this:

- Open /etc/systemd/system.conf as admin;
- **Uncomment** and change DefaultTimeoutStartSec=5s
- **Uncomment** and change DefaultTimeoutStopSec=5s

sudo systemctl daemon-reload

---

### Post by ommiorih on 2023-07-14
Ok thanks, I think I will just set:
DefaultTimeoutStopSec=10s

because starting any process is not a problem, and [it]("https://www.interkul.net/en/") could cause a lot of problems, so I just set stop time.

---

