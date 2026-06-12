---
title: "Software Update Problems - Lubuntu  14.04"
date: 2014-07-09
forum: General Help
---

### Post by mattw1 on 2014-07-09
I just ran the software updater and while I don't remember the exact updates that were performed, they both had to do with "Lubuntu base".  Anyway, since I performed those updates, several changes have occurred that are not for the better:

1-when the screensaver comes up after 10 minutes, I now have to enter my password to bring the desktop back even though I have that option unchecked in the preferences.
2-the power manager icon is now missing from the taskbar
3-even when I manually start the power manager, the power management settings that I have checked don't work, that is, the system won't suspend after 30 minutes of inactivity.

All of these preferences were working before doing the update.  Is anyone else having these problems?

Thx

[B]Matt W
Lubuntu 14.04
IBM Thinkpad t42
Pentium M
1.70 Ghz
768mb RAM
60gb HD[/B]

---

### Post by grier-devon on 2014-07-09
I would bet they will be fixed here soon, just make sure to report the problem so the dev's can see this.
[https://wiki.ubuntu.com/Lubuntu/ReportingBugs](https://wiki.ubuntu.com/Lubuntu/ReportingBugs)

---

### Post by linux_dream on 2014-07-09
I've got the same problem as number 1). I've tried everything I could to fix it (see [http://ubuntuforums.org/showthread.php?t=2233295](http://ubuntuforums.org/showthread.php?t=2233295)), but to no avail.

---

### Post by Rex Bouwense on 2014-07-09
Yes.  A lot of us are in the same boat.  A possible solution for 1. is to use Light Locker Settings.  That has worked for me.  However, reporting bugs is the way to get updates that work and don't break other things so +1 to the suggestion to report it.
[https://wiki.ubuntu.com/Lubuntu/ReportingBugs](https://wiki.ubuntu.com/Lubuntu/ReportingBugs)

---

### Post by linux_dream on 2014-07-09
> **Rex Bouwense said:**
> Yes.  A lot of us are in the same boat.  A possible solution for 1. is to use Light Locker Settings.  That has worked for me.  However, reporting bugs is the way to get updates that work and don't break other things so +1 to the suggestion to report it. [https://wiki.ubuntu.com/Lubuntu/ReportingBugs](https://wiki.ubuntu.com/Lubuntu/ReportingBugs)  I would appreciate if you could tell us how exactly to set the light locker settings?  Here's how I've set mine: [IMG]http://i.imgur.com/KPwmxhH.png[/IMG] but that didn't work.

---

### Post by Rex Bouwense on 2014-07-09
Turn enable light locker to off.  Apply and then close and you should be good to go.  The other two problems are still problems for me at least.

---

### Post by linux_dream on 2014-07-09
> **Rex Bouwense said:**
> Turn enable light locker to off.  Apply and then close and you should be good to go.  The other two problems are still problems for me at least.  Thank you very much! That also solved the problem when I suspend my computer, I'm not asked my password anymore...!!

---

### Post by Rex Bouwense on 2014-07-09
Great.  I hope that it helped the OP as well.  One down two to go.

---

### Post by linux_dream on 2014-07-10
Hmm actually that didn't fix the problem: after a reboot, although the Light Locker Settings shows that "Enable light locker" is set to "off", I'm asked my password after 10 minutes of innactivity...

---

