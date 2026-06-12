---
title: "Copy files on NTFS partitions?"
date: 2020-05-16
forum: General Help
---

### Post by lymphor on 2020-05-16
Hi,
I've recently upgraded from Ubuntu 16.04 to 18.04 and now suddenly I am unable to copy files on my NTFS partitions. Could anybody please help me?

Thanks in advance!

---

### Post by lymphor on 2020-05-16
I forgot to mention: everything worked fine after the upgrade for a few days. Then I had an upgrade on Windows 10 too (I'm running a dual boot) and the issue appeared.

---

### Post by yancek on 2020-05-16
You need to be more specific on what actually happens when you try to copy to an ntfs partition.  The fact that you did an upgrade on windows may be the problem or part of it as windows generally turns fastboot/hibernation back on during some updates.  Of course, you are not notified this will be done nor will you be asked.  If your Ubuntu is no longer abel to access/mount the ntfs partitions, that is a likely cause.  If you get some other problem, be specific about what it is.

---

### Post by JakcV on 2020-05-16
In Windows 10, there is a hybrid shutdown option which save the Windows state before shutdown for faster boot up. It maybe cause some issue.

---

### Post by CelticWarrior on 2020-05-16
This: [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by lymphor on 2020-05-17
Thank you very much CelticWarrior, this fixed the issue! :)
And thank you all for your answers and explanations!

---

