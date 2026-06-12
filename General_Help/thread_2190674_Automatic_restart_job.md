---
title: "Automatic restart job"
date: 2013-11-28
forum: General Help
---

### Post by obermensch on 2013-11-28
Hi everyone, i run a little mining pool for Yacoin.
The pushpool software seems to gown everytime i fall asleep and can't do maintainence.
so i have to restart it.

so i was wondering, how can i schedule e restart of the software every 2 hour?

the software itself get a new PID everytime i restart it.

the run command is "~/pushpoold/./pushpoold -E -F"

so basicly what i need, is that the software get killed every 2 hour, and automatic restarted =)

Thanks for any support on this!

---

### Post by ian-weisser on 2013-11-28
> **obermensch said:**
> 
so i was wondering, how can i schedule e restart of the software every 2 hour?


See man cron.

---

### Post by obermensch on 2013-11-28
Yes i know cronjobs, but i don't understand how i can cron a job to get killed, and started up at the same time.

---

### Post by ian-weisser on 2013-11-28
The cron job triggers a script.
The script ends the old job, starts the new job, logs the event, and performs any maintenance needed during the restart.

---

