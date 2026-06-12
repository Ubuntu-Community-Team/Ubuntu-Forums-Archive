---
title: "Closes after expanding"
date: 2012-12-07
forum: General Help
---

### Post by Pwnie2012 on 2012-12-07
Hi!
I have a problem, I just wanted to use WUBI for my Dualboot Ubuntu, but after WUBI "expands" the files, it just closes (no reboot dialog, no bootmanager entry). heres the logfile:

[http://pastebin.com/DysEf3R3](http://pastebin.com/DysEf3R3)

it says, it cant use some commands... If u can help me, post here... making the 100mb hdd online doesnt help.

---

### Post by bcbc on 2012-12-07
It means you have dynamic drives setup in windows. These aren't supported by linux. (The actual error is windows not letting you boot from a dynamic volume that won't yet be in existence at boot time).

---

### Post by Pwnie2012 on 2012-12-07
is there a possibility to convert it to a basic hdd without deleting the partitions?

---

### Post by bcbc on 2012-12-07
Yeah... you can use some partitioning tool. Others have used EaseUS free version to do it. e.g. here [http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)

I don't have exact details, but it sounds like it wasn't a big deal.

---

