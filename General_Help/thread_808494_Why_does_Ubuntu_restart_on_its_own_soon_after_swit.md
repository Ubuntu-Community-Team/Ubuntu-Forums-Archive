---
title: "Why does Ubuntu restart on its own soon after switch on occasionally?"
date: 2008-05-26
forum: General Help
---

### Post by Ashy72 on 2008-05-26
Hi I would like to know why Ubuntu sometimes automatically restarts itself soon after switch on? (usually once every week)

For information I have all software sources enabled and ubuntu is set up to check for updates once every week, which I manually install myself.

This question arises because I run ubuntu as a squeezecenter music server and it annoys me when I start playing my music and my player loses connection just after the first song because the server reboots then restarts. 

I know the restart is the cause of this because I see the entry in the ubuntu logs, where it says Ubuntu restarting, but as to why I do not know.

Thanks for advice on this.

---

### Post by werries on 2008-05-26
is this a laptop or desktop? you may have power management settings to change.
try turning it on, and watch it if it restarts. report whats happening to it before/during.

---

### Post by Ashy72 on 2008-05-26
Hello thanks for the quick reply,
The machine is a desktop computer I will turn it on now to investigate the power management settings... I will let u know the result.

---

### Post by Ashy72 on 2008-05-26
Power management is disabled eg set on the slider to Never. So I dont think this is the issue.

---

### Post by Ashy72 on 2008-06-02
Here is a copy of the syslog when the event happened.

May 30 20:50:09 Black-Widow syslogd 1.5.0#1ubuntu1: restart.
May 30 20:50:09 Black-Widow anacron[5654]: Job `cron.daily' terminated (mailing output)
May 30 20:50:09 Black-Widow anacron[5654]: Normal exit (1 job run)

Ideas anyone? Whats a cron.daily job?

---

