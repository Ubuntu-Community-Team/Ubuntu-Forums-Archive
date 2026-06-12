---
title: "Ubuntu 18.04 reboots around 23:30"
date: 2018-12-03
forum: General Help
---

### Post by mdadd on 2018-12-03
Hi,

my Ubuntu 18.04 keeps rebooting around 23:30 disrupting a long job that has never a chance to complete (it lasts longer than 24 hours and must be restarted from the beginning if interrupted).
I disabled chron, unattended updates, systemd.daily (apt-daily.service), and any kind of software updates.
I checked the RAM with one night of memtest86+, and made a CPU and overheating  stress test with the 'stress' package driving 4 cores, 8 threads, 100% for half an hour and temperature never got higher than 82degrees.
CPUs and cooling are working properly.
It looks the HW is ok and there should be no other, to my knowledege, source of reboot.
I disabled NIC interface too.

In spite of that it keeps rebooting at around the same time under light or heavy load conditions, doesn't matter.

I attach the /var/log/syslog where it looks there was a shutdown

Dec  2 23:27:56 lp-server systemd[1306]: Reached target Shutdown.

At reboot time there was plenty of free RAM and disk space-

Couldn't find anything else worth mentioning in other logs.

Maybe somebody with deeper knowledge than mine can make sense of the attached syslog and help me to get a clue.

Thanks a lot for any kind of help or hint.

---

### Post by freemedia2018 on 2018-12-03
What's this:

```
Dec  2 23:27:46 lp-server systemd[1306]: unity7.service: Service hold-off time over, scheduling restart.
```

---

### Post by mdadd on 2018-12-07
Hi freemedia2018 and thanks for your time and effort.

In the end I solved it: what you pointed out it's just one of a few services failing in the last 3 seconds and being rescheduled for restart.

They just fail again and again (a dozen of times) before an (automatic?) reboot sequence is performed.
I ruled out HW performing long and extensive tests and then I realized the job I was executing had a very strong spike of load (CPU, memory and lots of swapping) so I reduced its memory demand and allocated to it 7 of the 8 threads (4cores - 2 threads each).
It worked very well and cold complete the job in around 28 hours.

Thanks again and best regards.

---

