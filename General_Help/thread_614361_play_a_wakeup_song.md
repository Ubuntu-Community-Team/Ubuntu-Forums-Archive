---
title: "play a wakeup song"
date: 2007-11-15
forum: General Help
---

### Post by Tyke91 on 2007-11-15
Is there a way to create an alarm on my computer to play a song every day at 6:40 am (assuming the computer is on and logged in to my account) ?

---

### Post by geirha on 2007-11-15
Cron is your answer [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

If you have amarok running, with a "wake-up" playlist, you could have cron run something like "dcop amarok player play"

---

### Post by Tyke91 on 2007-11-15
```
no crontab for mykola - using an empty one
crontab: installing new crontab
"/tmp/crontab.iHOFgv/crontab":2: bad minute
errors in crontab file, can't install.
Do you want to retry the same edit? 

```

this is the error message that I am getting every time I try this.

I'm trying to enter this into cron to test

58 22 * * * amarok /home/mykola/Music/"Jonathan Coulton"/"Jonathan Coulton - Re; Your Brains.mp3"

---

### Post by Tyke91 on 2007-11-15
solved, you have to make a shell script for it to run first, you can't just type the command into cron.

---

