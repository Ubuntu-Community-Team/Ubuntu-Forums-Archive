---
title: "auto restart using gnome schedule, how?"
date: 2014-04-19
forum: General Help
---

### Post by KarlHungus on 2014-04-19
hi,i need to setup auto restart
is it possible using gnome schedule, how?

---

### Post by tgalati4 on 2014-04-19
You could set up a [cronjob]("https://help.ubuntu.com/community/CronHowto") and use the *shutdown* command.  Is this a one-time restart or a recurring restart (say once a day at 2 am)?

If a one-time restart use the *at* command.

---

### Post by KarlHungus on 2014-04-19
> **tgalati4 said:**
> You could set up a [cronjob]("https://help.ubuntu.com/community/CronHowto") and use the *shutdown* command.  Is this a one-time restart or a recurring restart (say once a day at 2 am)?

If a one-time restart use the *at* command.

i need a recurring restart...
i tried sudo gedit /etc/crontab
and put in
00  0   * * *    root   reboot
but my computer isn't rebooting at scheduled time for some reason

---

### Post by tgalati4 on 2014-04-19
Try choosing a time other than "00".  You should have several entries in your /etc/crontab for system maintenance.  Try to preserve them.  

It helps to restart the cron process after making changes:

```
sudo service cron restart
```

---

