---
title: "cron makes me grabby"
date: 2012-11-16
forum: General Help
---

### Post by rnerwein on 2012-11-16
i am running ubuntu 12.04
what i have done (in my useraccount) is:
crontab -e
insert the following line
2 * * * *    /home/richi/tmp/my_id

the script is owned by me and is executable

the file in /var/spool/crontabs was created 
ls -l /var/spool/cron/crontabs
-rw------- 1 richi crontab 1124 Nov 16 17:12 richi

but the result is that the script is running only every hour (looks like cron.hourly - but this directory is empty)

i also tried /etc/cron.allowd -> no change - cron is running only every hour.
whats going on ?

---

### Post by dannyboy79 on 2012-11-16
how often do you want it to run? and what is within the script?

---

### Post by rnerwein on 2012-11-16
> **dannyboy79 said:**
> how often do you want it to run? and what is within the script?

hello
it is just a test for me and i want to run it only 3 or 4 times.
the contens of the script is:

/usr/bin/id -a >>/home/richi/tmp/my_id.txt
/bin/date >> /home/richi/tmp/my_id.txt

and the permissions are:
ls -l my_id
-rwxr-xr-x 1 richi richi 82 Nov 16 16:09 my_id

by the side i ain't change anything in the configuration

---

### Post by dannyboy79 on 2012-11-16
have you successfully ran the script from the command line?

i believe you need 
```
#!/bin/bash
```
at the top of your script. also, what do you mean you want to run it 3 or 4 times? crontab needs specifics for how often you want to run it, whether it's once every 30 minutes or once every 10 minutes or what.

---

### Post by Slim Odds on 2012-11-16
Your cron job is set to run once an hour on the second minute of the hour. What did you expect?

man cron

---

### Post by VooDooSyxx on 2012-11-16
As has been said, your cron is set to run on the second minute of every hour. If you want it to run every 2 minutes or whatever, you would use a configuration like this

```

*/2 * * * * /home/richi/tmp/my_id

```

---

### Post by rnerwein on 2012-11-16
> **Slim Odds said:**
> Your cron job is set to run once an hour on the second minute of the hour. What did you expect?

man cron
here is the output of my script:

uid=1000(richi) gid=1000(richi) Gruppen=1000(richi),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare)
Fr 16. Nov 17:02:01 CET 2012
uid=1000(richi) gid=1000(richi) Gruppen=1000(richi),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare)
Fr 16. Nov 18:02:01 CET 2012
r
and here is the entry in my crontab:
2 * * * *    /home/richi/tmp/my_id

and i expected that means every two minutes and i want to have it run every two minutes ( just for testing)
what is my mistake ?

---

### Post by rnerwein on 2012-11-16
> **VooDooSyxx said:**
> As has been said, your cron is set to run on the second minute of every hour. If you want it to run every 2 minutes or whatever, you would use a configuration like this

```

*/2 * * * * /home/richi/tmp/my_id

```

ups
the error was between my ears. haven't use cron since years.
thanks 
i already call: crontab -r
:P

---

