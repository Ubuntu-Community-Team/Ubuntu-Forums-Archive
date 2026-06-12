---
title: "Laptop cpu frequency scaling on battery."
date: 2012-11-20
forum: General Help
---

### Post by PinkFloyd102489 on 2012-11-20
I have laptop-mode installed already but it doesn't seem to be functioning properly. Here is what I would like.

Plugged in = ondemand governor
On battery = conservative governor

It was changing like it should for a while but stopped all of a sudden. I figured out how to change the gov on all cores using the -r switch with cpufreq-utils, because my panel monitor was showing that only core0 was changing like it should.

I was thinking about making a hackish cronjob to check on_ac_power every 5 minutes and change accordingly, but there must be a better/easier way.



Thanks.

---

### Post by Linuxisfast on 2012-11-20
Remove Laptop mode and install Jupiter which does this automatically and does it well along with other tuning for battery life. You can find Jupiter at Web8upd ppa [https://launchpad.net/~webupd8team/+archive/jupiter](https://launchpad.net/~webupd8team/+archive/jupiter)

---

### Post by fyfe54 on 2012-11-21
+1 for Jupiter

---

