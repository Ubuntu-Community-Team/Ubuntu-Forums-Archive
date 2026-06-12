---
title: "Crontab: Execute every Sunday at 5AM"
date: 2008-01-08
forum: General Help
---

### Post by PinkFloyd102489 on 2008-01-08
I dont know what the setup would be for it. Some help?


This is what I have now:

0 5  0 * 0   stuffsync >/dev/null 2>&1

---

### Post by elspiko on 2008-01-09
```
00 5 * * 0 user command
```

---

### Post by Caligatio on 2008-01-09
I think elspiko has it *slightly* wrong

it's either:

00 5 * * 0 -u user command

or

00 5 * * 0 command

---

