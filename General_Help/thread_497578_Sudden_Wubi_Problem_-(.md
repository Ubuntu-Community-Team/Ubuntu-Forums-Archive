---
title: "Sudden Wubi Problem :-("
date: 2007-07-10
forum: General Help
---

### Post by kevinmedina on 2007-07-10
Hi

I have been ecstatic with the stability of my Feisty Fawn Wubi install :-) I really hope it gets bundled with Gutsy Gibbon

But, today I ran into a problem.  After turning on my Dell XPS M140 and booting into Ubuntu it would hang then after a few minutes bring me to the Debian BusyBox shell with the following error
```

/bin/sh: can't access tty: job control turned off
```

A few days ago I managed to get Compiz-Fusion along with Emerald Themes to boot up, which is the only major alteration I have made to system files.

I know that Wubi can get temperamental when performing a hard restart, which I may have unwittingly done again, albeit indirectly.  I had stuffed my laptop into my bookbag when leaving my house today, and apparently it was low on battery and still on.  By the time I got around to opening it up, it was dead and extremely hot.  It is after this that I found out that Ubuntu wasn't booting properly.  

I booted into M$ XP command and ran chkdsk /F on a reboot, then rebooted twice to get back into Ubuntu, but it resulted in the same problem.

Can anyone help me please? :confused:

---

### Post by ago on 2007-07-10
If you have an original MS cd try to run chkdisk from there. Also check the logs in /tmp/zenigata.log, look for lines that mention mounting of /media/host.

---

