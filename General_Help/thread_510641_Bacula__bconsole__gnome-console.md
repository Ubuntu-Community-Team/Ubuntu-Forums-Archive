---
title: "Bacula / bconsole / gnome-console"
date: 2007-07-26
forum: General Help
---

### Post by mmichalik on 2007-07-26
Hi everyone.

I've installed bacula in feisty and have one strange thing happening.

I can run btape -c /etc/bacula/bacula-sd.conf  and the test runs perfect.

I can make a backup and read the files off of the tape using tar cvf /dev/nst0 . without issue as well so, I know that the tape works and that it works through the bacula-sd.conf file.

The problem is when I try to run bconsole.  I get an error saying that it cannot communicate with the storage device.

I have gone through the bacula-dir.conf backwards and forwards and I can't see any thing wrong with it.  The Storage device is defined properly and called out in the two places in the file correctly as well.

Has anyone had any issues running bconsole or the gnome version of it?

any thoughts or help would be greatly appreciated.

Thanks,

Mike

---

