---
title: "Date and Time"
date: 2006-11-03
forum: General Help
---

### Post by 00Sven on 2006-11-03
I cannot use the "Adjust Date & Time" part of the clock.  All other parts work (Preferences, Help, About), but whenever I try to go to adjust it the bug reporting thing pops up instead.  My time is 1 hour behind what it should be.  Is there any way that I can fix this. 
P.S. I am running Edgy

---

### Post by taurus on 2006-11-03
Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo date MonthDayHourMinuteYear
(replacing Month, Day, Hour, Minute, & Year with a value...)
```

---

### Post by 00Sven on 2006-11-03
That did not really work.  It changed the time but then I restarted and it went back.  Also, after doing that every time that I tried to use "sudo" it said something like "timestamp to far in the future".  Is there a better solution?

---

### Post by wpshooter on 2006-11-03
What is your clock set to in the BIOS ?

---

### Post by bsussman on 2006-11-03
It your bios is set to UTC (GMT), is your timezone right?

go to System -> Time and Date to check/change

While you are there, turn on time sync if you want to stay accurate to world standard time.

---

### Post by wpshooter on 2006-11-03
> **00Sven said:**
> That did not really work.  It changed the time but then I restarted and it went back.  Also, after doing that every time that I tried to use "sudo" it said something like "timestamp to far in the future".  Is there a better solution?

How old is this computer ?

Is the BIOS on the latest and greatest version ?

---

