---
title: "Flashdrive files locked"
date: 2017-03-08
forum: General Help
---

### Post by Camilia on 2017-03-08
My flashdrive files got locked after I took it out of PC with windows 7 OS. Guess the PC was still on. Forum for windows gave me instructions to unlock the files. I was able to open the files on PC with windows but not on PC with OS 16.04. They just are opened in read mode. Suggestions?

sudo hdparm -r0 /dev/sdb. Read only = 0 but still on read-only mode

Ejected and reinserted it. Now it is working as should.

---

### Post by oldfred on 2017-03-08
Do you have Windows 8 or 10?
It seems to leave all NTFS partitions in hibernated state with its fast start up.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by Camilia on 2017-03-08
I have windows 7

---

