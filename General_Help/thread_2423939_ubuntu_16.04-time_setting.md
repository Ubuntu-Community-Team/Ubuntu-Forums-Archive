---
title: "ubuntu 16.04-time setting"
date: 2019-07-31
forum: General Help
---

### Post by bdubawoop on 2019-07-31
i have no date.time icon in settings
command line method produces "failed to create symbolic link 'etc/locatime' file exists.
this shud be simple

---

### Post by TheFu on 2019-07-31
more details please.

---

### Post by bdubawoop on 2019-07-31
well i still have no date/time icon in settings, & TWO printer icons.

i tried apt-get install unity-control-center but just got 'already current version'  msg & it then prompted me to apt-get autoremove old programs, which i did but that had no effect on problem.

however the time problem i fixed by googling.

had to tell timedatectl NOT to use UTC

i should mention this is an upgrade from 14.04 which wasn't smooth. had to go thru a few commands/reboots to get it to 16.04 but it seems ok now...aside from a few glitches like the above.

---

