---
title: "launch your control the startup"
date: 2013-01-10
forum: General Help
---

### Post by steph-ero on 2013-01-10
Hi all,

How to launch your control the startup of the machine in the rc.local under a different user name root: Example :: run virtual machines created under the user stephane.

thank you

---

### Post by Cheesemill on 2013-01-10
Use sudo. For example
```
sudo -u stephane command
```
Will run command as user stephane

---

### Post by steph-ero on 2013-01-10
I think I understand! must create a cron in / var / spool / crontab / on behalf of the user in question

---

### Post by steph-ero on 2013-01-10
thank you for the info, it was very simple. In fact I think we should also be able to run command at startup via a cron

---

