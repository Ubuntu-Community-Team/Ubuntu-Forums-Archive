---
title: "Cannot Locate Script"
date: 2018-07-25
forum: General Help
---

### Post by brenneke on 2018-07-25
Once upon a time I wrote and installed a small script to restart Network Manager. I no longer need this and would like to eliminate it from my system. I am receiving emails when this script has run:

```
Subject: Cron <root@JB> /home/jb/myscripts/restart-nm.sh
      To: root@localhost
```

I do find the myscripts folder but it is empty. I have searched for script name and can only find .restart-nm.sh.swp  in /home/jb. 

Any ideas as to what I am missing?

---

### Post by steeldriver on 2018-07-25
Possibly cron attempts to run it (even if it does not exist) either from root's crontab

```

sudo crontab -l

```

or from the system cron files

```

grep -r myscripts /etc/cron*

```

---

### Post by brenneke on 2018-07-25
I did more fumbling and found my network manager restart listed as a job when I ran sudo crontab -e. Maybe I did not write a script and set it up as a cron job, can't remember.

I did remove and save, probably gone now? Before posting I ran crontab -e, was not there.

I do not have enough knowledge on this to understand why I am seeing different jobs when running these commands.

Thanks.

---

### Post by brenneke on 2018-07-26
Can anyone explain the difference (aside from one being root) between using chrontab -e and sudo chrontab -e? Why are different jobs found using these commands?

---

### Post by steeldriver on 2018-07-26
Each (permitted) user has their own crontab, stored in /var/spool/cron/crontabs/*username* - including root

```

crontab -e

```

edits the crontab file for the invoking user, whereas

```

sudo crontab -e

```

edits root's crontab

---

