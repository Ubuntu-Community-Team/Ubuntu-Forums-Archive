---
title: "can't  write on ntfs partition"
date: 2018-08-24
forum: General Help
---

### Post by giuse1973 on 2018-08-24
hi
i have a laptop with 3 partition: ubuntu, ntfs date partition, windows10.
with ubuntu i can't write on ntfs date partition that i use for share my file with windows.

can you help me ?

---

### Post by oldfred on 2018-08-24
Almost always issue is Windows 10 fast start up which is just hibernation.
It checks the hibernation flag on all NTFS partitions.
And the Linux NTFS driver will not mount hibernated NTFS read/write or normal mount. It can be force mounted read only.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

