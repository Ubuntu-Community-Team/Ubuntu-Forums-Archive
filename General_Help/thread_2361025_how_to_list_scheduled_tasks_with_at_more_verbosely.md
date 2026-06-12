---
title: "how to list scheduled tasks with at more verbosely"
date: 2017-05-11
forum: General Help
---

### Post by pruda on 2017-05-11
Hi, I'm using at command to program tv recordings, but atq command is quite reserved on info, I see only time when something will be run, as who, but not what exactly. Is there some more clever way to list what is going to be started (except running sudo mc and browsing thru files in /var/spool/cron/atjobs using F3)? Thank you.

---

### Post by steeldriver on 2017-05-11
Have a look here:

[How to show a at scheduled command?](https://unix.stackexchange.com/a/360949/65304)

[What will at actually execute?](https://unix.stackexchange.com/a/94006/65304)

HTH

---

### Post by TheFu on 2017-05-11
From [https://serverfault.com/questions/174678/how-do-i-print-contents-of-at-jobs](https://serverfault.com/questions/174678/how-do-i-print-contents-of-at-jobs)
```
$ for j in $(atq | sort -k6,6 -k3,3M -k4,4 -k5,5 |cut -f 1); do atq |grep -P "^$j\t" ;at -c "$j" | tail -n 2; done
```

Is that helpful?

Sample output:
```
118     Thu May 11 17:00:00 2017 a thefu
tv-record.sh 9.2 30m

```
Recording ch9.2 for 30 minutes, starting at 1700.

---

### Post by pruda on 2017-05-11
Oh great, thank you. From the man description "cats the jobs listed on the command line to standard output" I did not get the meaning :-)

TheFu: that is amazing one liner, thank you!

---

