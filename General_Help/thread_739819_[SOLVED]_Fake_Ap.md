---
title: "[SOLVED] Fake Ap"
date: 2008-03-30
forum: General Help
---

### Post by nvysel24 on 2008-03-30
ok here is the problem i downloaded fake ap. which for those that dont konw what this tool is...it is a tool that creates thousands of fake aps so "you can hide in the open" i untared it and now its on my desktop in the folder. i cd into the folder and try to run sudo fakeap.pl it says command not found? what am i doing wrong ?  that is the name of the program and i am in the right folder so idk wat to do. im sorta a nub so ne advice would b lovley

---

### Post by dcstar on 2008-03-30
> **nvysel24 said:**
> ok here is the problem i downloaded fake ap. which for those that dont konw what this tool is...it is a tool that creates thousands of fake aps so "you can hide in the open" i untared it and now its on my desktop in the folder. i cd into the folder and try to run sudo fakeap.pl it says command not found? what am i doing wrong ?  that is the name of the program and i am in the right folder so idk wat to do. im sorta a nub so ne advice would b lovley

```
./fakeap.pl
```

---

### Post by danwood76 on 2008-03-30
you need to do ./fakeap.pl.
Running a command straight without a path makes it look into the $PATH variable for it (/bin, /sbin, etc) doing a ./ infront means it looks in your current directory.

---

### Post by nvysel24 on 2008-04-01
ok so i got fake ap working but its not working :( confusion
i got it to start creating fakeap but when i have my friend search for wireless sports it doesnt find none of the ones that im creating??!?!?
am i doing somthing w/ this script. here is my output of what i do then what it does

david@david-laptop:~$ sudo perl fakeap.pl --interface wlan0 
[sudo] password for david:
fakeap 0.3.1 - Wardrivring countermeasures
Copyright (c) 2002 Black Alchemy Enterprises. All rights reserved

Using interface wlan0:
Using 4 words for ESSID generation
Using 2 vendors for MAC generation
-------------------------------------------------------------------------
/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig0: ESSID=airport         chan=01 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig1: ESSID=Access Point    chan=06 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig2: ESSID=host            chan=09 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig3: ESSID=airport         chan=09 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig4: ESSID=tsunami         chan=09 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig5: ESSID=Access Point    chan=11 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig6: ESSID=airport         chan=05 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig7: ESSID=tsunami         chan=07 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig8: ESSID=tsunami         chan=06 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig9: ESSID=tsunami         chan=10 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig10: ESSID=host            chan=11 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig11: ESSID=Access Point    chan=11 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig12: ESSID=airport         chan=03 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig13: ESSID=airport         chan=09 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig14: ESSID=tsunami         chan=10 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig15: ESSID=airport         chan=07 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig16: ESSID=Access Point    chan=05 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig17: ESSID=airport         chan=07 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig18: ESSID=host            chan=05 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig19: ESSID=tsunami         chan=03 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig20: ESSID=host            chan=05 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig21: ESSID=Access Point    chan=09 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig22: ESSID=tsunami         chan=10 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig23: ESSID=airport         chan=11 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig24: ESSID=host            chan=01 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig25: ESSID=host            chan=05 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig26: ESSID=host            chan=03 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig27: ESSID=airport         chan=03 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig28: ESSID=Access Point    chan=02 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig29: ESSID=airport         chan=09 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig30: ESSID=Access Point    chan=04 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig31: ESSID=airport         chan=01 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig32: ESSID=tsunami         chan=08 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig33: ESSID=airport         chan=06 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig34: ESSID=Access Point    chan=05 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig35: ESSID=host            chan=10 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig36: ESSID=airport         chan=11 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig37: ESSID=host            chan=02 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig38: ESSID=Access Point    chan=08 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig39: ESSID=tsunami         chan=04 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig40: ESSID=airport         chan=03 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig41: ESSID=Access Point    chan=03 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig42: ESSID=host            chan=11 Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig43: ESSID=tsunami         chan=09 Pwr=

---

### Post by nvysel24 on 2008-04-01
ignore the last post and this post i jus created a new thread below i screwed the code up

---

