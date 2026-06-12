---
title: "Ubuntu 18.04 taking a long time to suspend"
date: 2019-06-09
forum: General Help
---

### Post by d0nkm3m3s on 2019-06-09
Hi, With my installation of Ubuntu 18.04 on my Lenovo T420 Laptop, whenever I close the lid, The system takes about 10-15 seconds or even longer to actually suspend. If I re-open the lid, the system goes back to the lock screen, but after a few seconds, the system abruptly suspends without warning, and when taken out of suspend, the system goes right back to where it was, any ways to fix this?

---

### Post by &amp;wP*!) on 2019-06-10
Copy and paste the stdout of **cat /proc/meminfo**, **free** and **systemd-analyze blame** - these might help us better to support you.

---

