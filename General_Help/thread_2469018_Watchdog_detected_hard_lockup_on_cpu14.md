---
title: "Watchdog detected hard lockup on cpu14"
date: 2021-11-17
forum: General Help
---

### Post by hugepickle on 2021-11-17
I'm repeatedly getting this after 1-2 days of my server running under load. It's running Ubuntu server 20.0.4. I've attached a picture of the screen with detail: [https://jzs-my.sharepoint.com/:i:/g/personal/julianzs_sjiconsulting_com/EegDJ5NImZBMjzeZj1ryPYEBuccTmGpLqwN9uO_nWDV-Cg?e=kkcpuF](https://jzs-my.sharepoint.com/:i:/g/personal/julianzs_sjiconsulting_com/EegDJ5NImZBMjzeZj1ryPYEBuccTmGpLqwN9uO_nWDV-Cg?e=kkcpuF).

Thanks in advance!

---

### Post by Doug S on 2021-11-17
The information from your screen shot should also be in your /var/log/kern.log file. Extract the information and put it here, look for the first occurrence in the log, the one where the kernel is NOT tainted.

Also, there is [a handy forums script]("https://github.com/UbuntuForums/system-info") that will give us a lot of information about your system that might help. Run it and allow it to put the report on pastebin and give us the link or put the report here as an attachment.

---

