---
title: "time and date settings"
date: 2014-03-17
forum: General Help
---

### Post by rburkartjo on 2014-03-17
i have linux on a partition and win7 on the other. never had a problem with time and date settings when switching to either partition.  i recently put peppermint linux on a 32g stick. if i boot into peppermint with the stick the time is still right. however once i reboot my system directly into my hard drive after using peppermint the clock in lubuntu is off by 5 hours. and idea how to correct. tks

---

### Post by Impavidus on 2014-03-17
Windows interprets the time from the bios clock as local time, Lubuntu has been set to do the same, peppermint maybe not? As result, on shutdown peppermint may set the bios clock to Greenwich time, causing the time in Lubuntu to be off. I don't know why the time is not off in peppermint after a previous boot in Lubuntu. Maybe it automatically synchronises the clock with a time server?

The setting is in /etc/default/rcS. UTC can be yes or no.

---

### Post by Bashing-om on 2014-03-17
rburkartjo; Hi !

We meet again.

I would suspect ("lubuntu is off by 5 hours. ") the differential in the hardware clock/system.
To tell your peppermint system that the hardware clock is set to 'local' time:

edit /etc/default/rcS
add or change the following section :
"# assume that the BIOS clock is set to UTC time (recommended)
UTC=yes"
# Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no -> elsewise
(needless to say compare ubuntu's file to that of peppermint)
You need to have root privileges, which means using sudo.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by rburkartjo on 2014-03-17
bash tks will try that in the morning and mark thread solved if works and it should.

---

### Post by rburkartjo on 2014-03-18
bash tks . this line was also in pepperment it was set to no just changed to yes

# assume that the BIOS clock is set to UTC time (recommended)
UTC=yes"

however when i added 
# Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no -> elsewise

it crashed peppermint and had to do new install. no big deal. this time i just changed no to yes and didnt install the second. worked like a charm

---

### Post by Bashing-om on 2014-03-18
rburkartjo; Great.

All good in the end, and no blood spilled.

[INDENT][INDENT]That's a good day
[/INDENT][/INDENT]

---

### Post by rburkartjo on 2014-03-18
yup

---

