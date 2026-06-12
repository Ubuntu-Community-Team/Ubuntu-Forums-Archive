---
title: "Bi-weekly anacron entry"
date: 2012-11-24
forum: General Help
---

### Post by CaptainMark on 2012-11-24
Is it possible to create a anacron entry that will run every other week or is it either weekly or monthly. Or is there a workaround or trick/tip  for getting a anacron job to run biweekly

---

### Post by dcstar on 2012-11-24
> **CaptainMark said:**
> Is it possible to create a anacron entry that will run every other week or is it either weekly or monthly. Or is there a workaround or trick/tip  for getting a anacron job to run biweekly

0 0 */14 * *
Runs at midnight every 14 days.
```

man cron
```

---

### Post by CaptainMark on 2012-11-25
I wanted anacron specifically, it's for a computer which will rarely be on at midnight
Edit: Or in fact any specific time

---

### Post by raja.genupula on 2012-11-25
[http://www.it.uc3m.es/marcos/doc/miniHOWTOs/miniHOWTO-Use_anacron_as_non-root_user.html](http://www.it.uc3m.es/marcos/doc/miniHOWTOs/miniHOWTO-Use_anacron_as_non-root_user.html)

---

