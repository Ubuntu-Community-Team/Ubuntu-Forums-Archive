---
title: "/ filesystem went read-only"
date: 2013-10-07
forum: General Help
---

### Post by Vladimir_Melnik on 2013-10-07
Hello!

I have a server which works as an iSCSI-target. All the data is located on its drives, but the operating system (Ubuntu 10.04) is installed on an USB stick. Now I know it was a bad idea, because yesterday the / filesystem has been marked as read only.

I didn't reboot it, but I runned fsck -y. It has found a lot of errors and now it doesn't se&#1077; any files (even /bin/ls).

The server is still working as an iSCSI-target, but I'm not sure it will boot for the next time.

How probably is it? Will it boot after that or have I to reinstall the operating system?

Of course, I'm going to prepare another USB stick with the operating system installed, but the server is a bit far away and it would be nice to get to know more about other people's experience.

Thank you.

---

