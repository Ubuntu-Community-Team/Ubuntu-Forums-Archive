---
title: "Filezilla slower on Linux (compared to Windows)"
date: 2016-05-22
forum: General Help
---

### Post by faster7on7windows on 2016-05-22
[SIZE=2]**_Windows_** Filezilla 3.17.01
Filezilla ftp and sftp download at 12 megabytes (96 megabits) per second no matter how many files I download. If I download 1 file then it downloads at 12 megabytes. 10 files download at about 1.2 megabytes each. Filezilla version is 3.17.01 but I also had the same speed with previous versions last year.

**_Ubuntu 16.04 64 bit _** Filezilla 3.15
-Filezilla sftp and regular ftp are limited to 800KB/s per file. If I download 10 files at once then I can get 8MB/s total. If I download only 1 file then download speed is stuck at 800KB/s (100% of the time no matter what seedbox I use). 

**_Similar posts of Filezilla being slower on Linux_**
[https://forum.filezilla-project.org/viewtopic.php?t=32022](https://forum.filezilla-project.org/viewtopic.php?t=32022)
[https://bbs.archlinux.org/viewtopic.php?id=198428](https://bbs.archlinux.org/viewtopic.php?id=198428)
[SIZE=4][/SIZE][/SIZE][COLOR=#000000][SIZE=6]
_**Solved by modifying sysctl with:**_[/SIZE][/COLOR][SIZE=6]
[COLOR=#323D4F][FONT=Lucida Grande]sudo sysctl -w net.ipv4.tcp_rmem='40960 873800 62914560'[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]sudo sysctl -w net.core.rmem_max=8388608[/FONT][/COLOR][/SIZE]

---

### Post by jim_deadlock on 2016-05-23
It's clearly an issue with Filezilla rather than Ubuntu so just use something else instead. Have you tried the 'Connect to Server' option within Nautilus (Files)? I find it much more convenient than a standalone FTP app. There is also the FireFTP Addon for Firefox which is pretty cool too.

---

### Post by faster7on7windows on 2016-05-24
> **jim_deadlock said:**
> It's clearly an issue with Filezilla rather than Ubuntu so just use something else instead. Have you tried the 'Connect to Server' option within Nautilus (Files)? I find it much more convenient than a standalone FTP app. There is also the FireFTP Addon for Firefox which is pretty cool too.
Thank you for the reply!

I posted on the Filezilla forum and the administrator said it is an issue with the Linux Kernel.
[COLOR=#323D4F][FONT=Lucida Grande]"There is a bug in the Linux kernel. For some reasons programs requesting a large TCP receive buffer actually get a smaller TCP window scale factor than programs not specifying a receive buffer at all."[/FONT][/COLOR]

Modifying sysctl fixed the problem:
[COLOR=#323D4F][FONT=Lucida Grande]sysctl -w net.ipv4.tcp_rmem='40960 873800 62914560'[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]sysctl -w net.core.rmem_max=8388608[/FONT][/COLOR]

Source:
[https://forum.filezilla-project.org/viewtopic.php?f=2&t=40513&sid=d1fda044b126eb6318aa2f5da7454e14](https://forum.filezilla-project.org/viewtopic.php?f=2&t=40513&sid=d1fda044b126eb6318aa2f5da7454e14)

---

### Post by jim_deadlock on 2016-05-24
That thread there is very interesting, thanks for linking it. I still think you should try Nautilus' built-in FTP tool, it's so nice dealing with remote files the same way as local ones.

---

### Post by jim_deadlock on 2016-05-24
FYI, the commands don't persist after reboot so you can add them at the end of /etc/sysctl.conf (note: remove '')

```
net.ipv4.tcp_rmem=40960 873800 62914560
net.core.rmem_max=25000000
```

---

