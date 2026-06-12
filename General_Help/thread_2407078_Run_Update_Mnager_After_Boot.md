---
title: "Run Update Mnager After Boot"
date: 2018-11-29
forum: General Help
---

### Post by Quarkrad on 2018-11-29
I have a number of machines (that I look after) that appear to be not on long enough to be up to date (over time). Is it possible to configure the system such that the update manager will *run/check/prompt user* say, three minutes, after the Desktop boot?

---

### Post by Quarkrad on 2018-12-05
Can you fixed the time Unattended Upgrade kicks in(?) - I believe at the moment it is random.  What happens if the randoms times never kick in because the machine is switched off too soon? (Logically the machine is not updated and hence vulnerable).

---

### Post by Dennis N on 2018-12-05
> **Quarkrad said:**
> Can you fixed the time Unattended Upgrade kicks in(?) - I believe at the moment it is random.  What happens if the randoms times never kick in because the machine is switched off too soon? (Logically the machine is not updated and hence vulnerable).

Are you using 16.04 or 18.04? In 18.04, I've checked from time to time to see when it does the unattended upgrades, and evidence so far suggests its done right after login:

From this morning history.log:

```
Start-Date: 2018-12-05  06:43:24
Commandline: /usr/bin/unattended-upgrade
Upgrade: poppler-utils:amd64 (0.68.0-0ubuntu1, 0.68.0-0ubuntu1.2), libpoppler-qt5-1:amd64 (0.68.0-0ubuntu1, 0.68.0-0ubuntu1.2), libpoppler-glib8:amd64 (0.68.0-0ubuntu1, 0.68.0-0ubuntu1.2), libpoppler79:amd64 (0.68.0-0ubuntu1, 0.68.0-0ubuntu1.2)
End-Date: 2018-12-05  06:43:26
dmn@Roxanne:~$ uptime
 07:42:58 up  1:00,  1 user,  load average: 0.04, 0.16, 0.20


```
using uptime output,  7:42 am - 1.00 uptime = 6:42 am start up time, so update started about 1 minute later (6:43:24 am), which is typical of what I have seen. 

I do recall problems like you describe when using 16.04 early on. Seemed like it didn't check at all or there was a long delay. But recently installed a system from new 16.04.5 iso and it seems to be set to work like 18.04, so that was nice.

---

### Post by Quarkrad on 2018-12-06
The machine of concern is running 16.04 - I intend to upgrade it but as it is used for business I am leaving things as they are.  If it is better to move to 18.04 (re running unattended upgrades) then I will move to 18.04.

---

