---
title: "Timed logon period"
date: 2007-08-10
forum: General Help
---

### Post by BruceWilkinson on 2007-08-10
Is there a way to force logoff? I have a public workstation running Ubuntu. It's intended for checking email with a 15 minute logon duration. Can I force users off after 15 minutes?

Bruce

---

### Post by imbjr on 2007-08-10
Look into having a cron job run a script such as:

#/bin/sh
skill -KILL -u <your user name>

I don't have this croned, but I do use it with a launcher icon in my son's account so he can logout but not switch the PC off.

---

### Post by BruceWilkinson on 2007-08-14
That doesn't provide a solution to my problem. I can't sit and monitor, and force off users every 15 minutes. I'm looking for a way to automate it, i.e. the user logs on, the timers starts, 15 minutes later, the user is logged off so another user can check email.

Bruce

---

