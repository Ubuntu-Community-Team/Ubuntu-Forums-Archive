---
title: "Cronjob not honoring time range"
date: 2021-05-07
forum: General Help
---

### Post by onlineguy on 2021-05-07
Hi,

I created a crontab entry as follows:

```
*/10 06-21 * * * /usr/bin/python3 /home/ubuntu/repos/vacc_check/main.py >> /home/ubuntu/cron-log.txt
```

```
ubuntu@ubuntu-lxc:~$ timedatectl
                      Local time: Fri 2021-05-07 21:59:22 CEST
                  Universal time: Fri 2021-05-07 19:59:22 UTC
                        RTC time: n/a
                       Time zone: Europe/Berlin (CEST, +0200)
       System clock synchronized: no
systemd-timesyncd.service active: yes
                 RTC in local TZ: no
```

I can see in cron-log.txt that the job is called after 9 pm, latest run is at 9:50 pm (~current time), why is that?

---

### Post by Tadaen_Sylvermane on 2021-05-07
You are setting it to include every 10 mins for 9pm as well. This would be the way to do it.

```
*/10 06-20 * * * /script
```

The last run will be at 8:50 pm if I'm understanding your question correctly.

---

