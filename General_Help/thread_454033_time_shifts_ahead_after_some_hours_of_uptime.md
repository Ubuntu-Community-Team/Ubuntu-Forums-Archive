---
title: "time shifts ahead after some hours of uptime"
date: 2007-05-25
forum: General Help
---

### Post by forger on 2007-05-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/104091](https://bugs.launchpad.net/ubuntu/+bug/104091) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Problem: The clock shifts some minutes/hours ahead after some hours of uptime :KS

 I want to say that the clock worked perfectly in edgy (even without , it works in xp and it doesn't work as expected on ubuntu feisty. I reverted back to edgy to see if it was hardware-related, but it was still working in ubuntu edgy :o
 To track this, I've used:
```
hwclock && date
```

There was no *big* change in the hardware clock and software clock, only some seconds difference. So I was told that it doesn't have to do with GNOME, but with something else.

 Some times I think I'm prone to breaking stuff.. This ubuntu feisty I'm currently using is merely a fresh install (formatted the root partition and installed)
 I have filed a bug at launchpad: [https://bugs.launchpad.net/ubuntu/+bug/104091](https://bugs.launchpad.net/ubuntu/+bug/104091)
 If someone has the same problem, and they know how to get the necessary information, please do! Or guide me to find some time logs, **please**!

Note: This happens with and without the ntp, so I guess (at least in my system) ubuntu feisty fails to detect the correct timing or something.

Edit: I even tried the ntpdate in /etc/cron.daily/, but the time still manages to go nuts (as in go ahead in time) in a day!

---

### Post by forger on 2007-05-25
anyone?

here's the time shifting from the time of posting the letter (i used **sudo ntpdate europe.pool.ntp.org**):
```
Fri 25 May 2007 11:51:25 PM CEST  -0.624843 seconds
Sat May 26 00:10:46 CEST 2007
```

edit: this time i tried changing the clock manually backwards, i never tried that, maybe that will calm it down :)

---

