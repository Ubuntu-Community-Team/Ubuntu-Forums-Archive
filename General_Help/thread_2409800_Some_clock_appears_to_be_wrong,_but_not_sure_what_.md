---
title: "Some clock appears to be wrong, but not sure what or how"
date: 2019-01-07
forum: General Help
---

### Post by sfatula on 2019-01-07
So, this happens from time to time on a reboot, what could be the cause?

I had 3 boots today. Here's some syslog excerpts, the most important is the last one:

Jan  6 13:00:33 Emby-Games kernel: [    0.064274] RTC time: 19:00:28, date: 01/06/19

The above looks close at least, what is RTC time (from BIOS?). I am CDT, so, 6 hours earlier than UTC.

Jan  6 13:14:18 Emby-Games kernel: [    0.068275] RTC time: 19:14:12, date: 01/06/19

Again, the time is close, while the first once was 5 seconds difference, this second one is 6 seconds, could be rounding.

Jan  6 13:29:18 Emby-Games kernel: [    0.064276] RTC time: 13:47:40, date: 01/06/19

Ooops, so, the actual time was in fact 13:47:40 as the RTC says, so, since this is part of the boot process, where does the 13:29 come from, and, where does the 13:48 come from? Did I perhaps do something dumb like set the time incorrectly? If I did, later on, 

Jan  6 13:48:50 Emby-Games systemd-timesyncd[663]: Synchronized to time server 91.189.94.4:123 (ntp.ubuntu.com).

Does systemd-timesyncd set all the clocks, so, from that point forward, all will be well?

---

### Post by CatKiller on 2019-01-07
RTC is the Real Time Clock: the time that your motherboard thinks it is. Linux sets the motherboard clock to UTC and then uses the timezone offset to display the local time.

There's some logical reason for doing it that way round, but I can't remember what it is.

---

### Post by sfatula on 2019-01-08
Ok, so, why this line:

[COLOR=#000000]Jan 6 13:29:18 Emby-Games kernel: [ 0.064276] RTC time: 13:47:40, date: 01/06/19

If RTC = hardware clock, then, where did 13:29:18 come from on bootup? That is what I do not understand. [/COLOR]

---

