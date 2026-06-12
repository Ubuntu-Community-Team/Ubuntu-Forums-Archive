---
title: "Cron"
date: 2004-11-03
forum: General Help
---

### Post by grj on 2004-11-03
I have set up a cron job to execute the following command:

0 5 * * * calendar -l 14

which should display task in my calendar program from the current day to 14 days into the future. The problem is it runs but does not display to stdout. If I add a pipe to the end to send the out put to a file, it creates the file with the expected data.

Anyone know how to make a cron job write to stdout?

Thanks,

grj

---

