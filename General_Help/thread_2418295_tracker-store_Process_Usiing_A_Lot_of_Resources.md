---
title: "tracker-store Process Usiing A Lot of Resources"
date: 2019-05-04
forum: General Help
---

### Post by scpatl4now on 2019-05-04
It seems to increase the longer I go between boots, but 37+ GiB seems excessive for virtual memory and still using 400+ MiB in memory.  I dont recall ever seeing this in my process list prior to upgrading to 19.04 from 18.04.  I just rebooted and now it is
437 MiB VM
11 MiB memory

What does this process do?

---

### Post by Rubi1200 on 2019-05-04
Indexes emails, files etc. for faster searching.

Recent problem reported and seemingly solved:
[https://unix.stackexchange.com/questions/482390/usr-lib-tracker-tracker-store-causes-very-heavy-cpu-load-on-debian-buster](https://unix.stackexchange.com/questions/482390/usr-lib-tracker-tracker-store-causes-very-heavy-cpu-load-on-debian-buster)

Definitely recommend you make a good backup of your data before proceeding with fix suggested.

Hope it helps.

---

