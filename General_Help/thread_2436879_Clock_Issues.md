---
title: "Clock Issues"
date: 2020-02-14
forum: General Help
---

### Post by mraamohamed on 2020-02-14
Hello does anyone else have this problem.  After coming out of a bootup and use Ubuntu then go to windows 10 my closck is WAY off like a day off, have to go into setting to fix this anyone else experience this issue, and fix?

Thanks

---

### Post by yetimon_64 on 2020-02-14
Windows uses local time, ubuntu uses UTC, this is what causes the differences you are seeing.
When you boot into ubuntu, it sets the system clock to UTC and then when you use Windows it sees the time and thinks that is local time, which is way off.

 You can either set Windows to use UTC or Ubuntu to use local time to get them to align though it is probably easier to get Ubuntu to use local time with the next command in the terminal ...
[FONT=&amp]```
sudo timedatectl set-local-rtc 1 --adjust-system-clock
```[/FONT]This should then bring the two systems into alignment for the time.

Regards, yeti.

---

