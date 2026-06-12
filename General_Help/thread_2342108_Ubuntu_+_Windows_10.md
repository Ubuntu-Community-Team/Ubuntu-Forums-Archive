---
title: "Ubuntu + Windows 10"
date: 2016-11-03
forum: General Help
---

### Post by mayagrafix on 2016-11-03
I used Ubuntu on DVR to boot a PC with Win10 OS and was not allowed to copy-paste some docs from the Win32 folder. How is this possible? When I boot from a DVD, do the OS files on a HDD remain active?

---

### Post by Impavidus on 2016-11-04
Could you mount the Windows file system? Have you tried mounting it read-only using command line?

Windows 10 keeps its file systems mounted after "shutdown" to hide the fact that it boots so slow.

---

### Post by Bucky Ball on 2016-11-04
Just to check: you are not actually using 15.04 are you??? That is well EOL.

Boot to Windows and check you have hibernation off.

---

### Post by oldfred on 2016-11-04
Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

