---
title: "Memory Usage (Yes, I understand about Cached)"
date: 2007-10-23
forum: General Help
---

### Post by Aikon- on 2007-10-23
I have a system with Ubuntu 7.10 installed with 1.5GB RAM. System Monitor, on the Resources tab, shows a pretty consistent ~700MB user memory and 50MB used swap. I'm fairly sure this has nothing to do with disk caching since A) "user memory" in system monitor doesn't include disk caching and B) cat /proc/meminfo says that all but a few MB of memory are being used, ~700 for user memory and ~750 for cache (which seems to agree with the System Monitor graphs).

My problem is that I can't find that memory usage. In Dapper, I was able to directly map the user memory to the processes list and get numbers that matched or were very close. However, with ~700MB being shown as actually *in use*, I only count about 250MB being used. I have checked "all processes" under View.

Any suggestions as to how I can find this "missing" memory?

-Aikon

---

### Post by Aikon- on 2007-10-23
Hmm.. I may have just solved this for myself. It seems I was adding up the "Memory" column, while what I *should* have been adding up was the "Resident Memory" column.

Most are on the same order, except for "Xorg", which showed "0 bytes" in the memory column but shows "378.9MB" in the resident memory column. Seems like a lot..

-Aikon

---

### Post by Aikon- on 2007-10-26
For reference, I just rebooted my system and I show 250MB of user memory and 0 bytes of swap used... It seems like memory usage is creeping up wit uptime?

---

