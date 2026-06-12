---
title: "Time jump after installing ntpd"
date: 2014-05-09
forum: General Help
---

### Post by abraham5 on 2014-05-09
After reading [this article]("https://help.ubuntu.com/12.04/serverguide/NTP.html") I was so exsited that I immideitly got ntp installed using
```
sudo apt-get install ntp
```

Now everything is absolutely fine with the general performance of the application, the only drawback is that eventhough in '/etc/default/rcS'; 'UTC=no' is set, (and I want it that way cause I am dualbooting), everytime I start my system my clock is set to UTC time instead of local time, and the only way to correct that is to give ntp an internet connection. 

How can I correct this?

Also is running ntpdate equal to ntpdaemon? I mean in the sense that ntpdaemon keeps a record of the errors and so in the future even if it doesn't have Net connection, it would be able to accuratly correct the time based on the records. Should I just remove ntp?

Oh, by the way I am NOT on a server.

---

### Post by tgalati4 on 2014-05-09
There are a few things that you can do.  Look in your BIOS for a setting--"Store time in UTC".  Change Windows to use UTC with a user-defined time zone.  You will have to search for how to do that.  ntp requires a network connection--it is afterall a "network time protocol".

ntpdate just updates the date and time once--whenever it is called, usually at boot.

Getting time to display correctly in dual boot is a common problem.

---

### Post by abraham5 on 2014-05-10
I just figured what the problem was, this actually only happens if the system gets restarted abnormally (like after a freeze), but in normal conditions it would not happen, even if there is not Net access.

---

