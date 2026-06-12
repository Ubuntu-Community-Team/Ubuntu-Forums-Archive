---
title: "cannot get a cronjob to execute"
date: 2007-02-23
forum: General Help
---

### Post by neill on 2007-02-23
hi

for some reason i can't get a cronjob to run

from the CLI

f-prot /home | mail -s "f-prot" root

does exactly what i expect - it mails me the output from the f-prot command

however ...

when i run gksudo gnome-schedule (i'm an ex windows GUI addict sadly) and add exactly the above command it won't run

originally i got a 'command not found error' emailed from cron - so i symlinked f-prot into my PATH (/bin)

now i get a 'contents not found error' which i guess is mail moaning it has nothing to pipe

in any case the f-prot command isn't being executed

any thoughts as to why ?

how do i go about investigating this ?

thanks

neill

---

### Post by keithweddell on 2007-02-23
You probably need the full path to f-prot.  Try entering "which f-prot" and use the result in the cron job.

Keith

---

### Post by neill on 2007-02-23
OK thanks

will try that tonight when i get home from work

---

### Post by neill on 2007-02-24
yep you were absolutely right  - full/path/to/f-prot needed

wonder why ??

thanks anyway for your help

---

