---
title: "Clock Setting Changes on Dual Boot System"
date: 2018-02-18
forum: General Help
---

### Post by rbscairns on 2018-02-18
I run Windows XP and Lubuntu 16.04 on a dual boot system. I am having a problem with the time setting when I reboot from Lubuntu to XP.

[LIST]
[*]My time zone on both operating systems is set to UTC+8hr.
[*]Upon booting into Lubuntu and the correct local time is displayed.
[*]If I then reboot into XP, the time displayed is UTC (not local UTC+8hr).
[*]In XP I check the date/time window and find that the time zone is still set for UTC+8hr but the time displayed is UTC.
[*]I then reboot back into Lubuntu and the correct local time (UTC+8hrs) is displayed.
[*]I reboot into XP and reset the time to local and it is displayed correctly.
[*]If I then reboot into XP, the correct local time is displayed.
[*]I reboot back into Lubuntu and the correct local time is displayed.
[*]I reboot into XP and again the time displayed is UTC (not local UTC+8hr). This requires me again to reset the correct time in XP.
[/LIST]

Is there a way to prevent Lubuntu from somehow changing my local time back to UTC when I boot into XP?

I am using Lubuntu more and more now as I learn to fix the problems I have using it. I still need XP to use my printer and scanner (i have yet to get either to work in Lubuntu) and I have a couple of specialist programmes required for my work that only operate in XP.

---

### Post by rbmorse on 2018-02-18
This should help you:

[https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/](https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/)

---

### Post by rbscairns on 2018-02-18
Thank you rbmorse.
```
timedatectl set-local-rtc 1 --adjust-system-clock
```
worked like a charm.

I wish I could be as helpful to others as others have been so helpful to me.

---

