---
title: "Duel boot complications"
date: 2019-10-03
forum: General Help
---

### Post by tarundas on 2019-10-03
I am having duel boot system (Windows 10 and Ubuntu 18.4) for a while. If I 'Shut down' my computer from Windows and then reboot in Ubuntu I won't have write permission on other partition of the same drive. I can't save any file on my 2nd partition which is NTFS. But if I 'Restart' my Windows and then boot in Ubuntu I would have all the rights on my NTFS partition.  This is the 2nd hard disk I am having the same problem. Why this is happening and how to fix it? Thank you.

---

### Post by coffeecat on 2019-10-03
Have you disabled fast startup in Windows? You need to if you want to mount NTFS partitions from Ubuntu and have read-write permissions. If you have fast startup enabled (the default in Windows), shutting down doesn't shut down properly - it's a sort of hybrid hibernation and shutdown - and leaves the filesystem in a state that cannot be accessed read-write from Linux. It's odd that with a restart you are not having this problem.

In any event, check this link, and make sure you have fast startup in Windows **disabled**:

[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by tarundas on 2019-10-03
Thank you very much. After disabling fast startup in Windows the problem is solved.

---

