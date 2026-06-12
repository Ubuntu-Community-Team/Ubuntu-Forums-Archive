---
title: "monitor if power goes out using a laptop"
date: 2014-01-03
forum: General Help
---

### Post by bigrockcrasher on 2014-01-03
I am currently trying to figure out how to determine when a laptop is recieving power from a wall output so i can record when the power goes out. There is probably a device i can buy that i can use but i have limited resources.

---

### Post by tgalati4 on 2014-01-03
Install acpitool, open a terminal:

```
sudo apt-get install acpitool
acpitool -a
```

You can run a cronjob that uses *acpitool -a* every 5 minutes and if other than "online" you can write a *logger* line.

I will leave it to you (or others) to figure out a script to do that.

Pseudo code:

Run acpitool -a
If "online" then exit 0 (no error status)
else if "offline" (a presumed power outage) then write a syslog entry using logger--"The power is probably out."  exit 1 (error status)

--------------------------

A more difficult way to handle this is to use *power-status-change* and run a upstart script using it:

Psuedo code:

Put upstart script in correct location.
On power-status-change run logger "Power is probably out."

The advantage of using upstart/init is you get a finer detection of when the event happens--if you need finer than 5-minute detail.

---

