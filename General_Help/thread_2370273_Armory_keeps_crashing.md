---
title: "Armory keeps crashing"
date: 2017-09-01
forum: General Help
---

### Post by abasel on 2017-09-01
I am running Ubuntu 16.04.3 LTS and have installed armory_0.96.2-ubuntu14.04_amd64.deb  

When I run Armory it appears in launcher for a few minutes and then crashes.

I am not sure which log file to look at but sudo tail  /var/log/apport.log returns the following:

> ERROR: apport (pid 4055) Sat Sep  2 01:04:19 2017: called for pid 4041, signal 4, core limit 0
ERROR: apport (pid 4055) Sat Sep  2 01:04:19 2017: script: /usr/lib/armory/ArmoryQt.py, interpreted by /usr/bin/python2.7 (command line "python2 /usr/bin/../lib/armory/ArmoryQt.py --offline")
ERROR: apport (pid 4055) Sat Sep  2 01:04:19 2017: debug: session gdbus call: (true,)

ERROR: apport (pid 4055) Sat Sep  2 01:04:19 2017: this executable already crashed 2 times, ignoring
ERROR: apport (pid 14263) Sat Sep  2 01:10:38 2017: called for pid 14249, signal 4, core limit 0
ERROR: apport (pid 14263) Sat Sep  2 01:10:38 2017: script: /usr/lib/armory/ArmoryQt.py, interpreted by /usr/bin/python2.7 (command line "python2 /usr/bin/../lib/armory/ArmoryQt.py --offline")
ERROR: apport (pid 14263) Sat Sep  2 01:10:38 2017: debug: session gdbus call: (true,)

ERROR: apport (pid 14263) Sat Sep  2 01:10:38 2017: this executable already crashed 2 times, ignoring


How do I work out what the issue is and how to fix it?

---

### Post by ajgreeny on 2017-09-01
It may not show you more than you already have seen but it's worth starting it from terminal with whatever is the appropriate command to see if that gives you any more info.

---

### Post by abasel on 2017-09-01
All I get when running from terminal is "Illegal instruction (core dumped)"

I am going to try building from scratch.

---

### Post by abasel on 2017-09-01
I uninstalled and then built from scratch using [https://www.bitcoinarmory.com/building-from-source/]("https://www.bitcoinarmory.com/building-from-source/") and it all worked

---

### Post by ajgreeny on 2017-09-02
Great!
Please mark as SOLVED from Thread Tools menu up top.

---

