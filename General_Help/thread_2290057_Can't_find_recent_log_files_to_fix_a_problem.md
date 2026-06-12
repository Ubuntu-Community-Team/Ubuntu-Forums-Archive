---
title: "Can't find recent log files to fix a problem"
date: 2015-08-09
forum: General Help
---

### Post by Gnusboy on 2015-08-09
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]
I'm having a problem locating my current log files. When I go to a folder like **var log apt** I see many separate files starting with  "History.log.1.gz" and continuing through "History.log.12.gz" 
When I open them they show what appear to be boot files, but they are several months old and not current. Here is an example:
                        **Start-Date: 2014-10-01  10:02:53**[B]Commandline: aptdaemon
role='role-commit-packages' sender=':1.78'[/B][B]Upgrade: libvncserver0:amd64 (0.9.8.2-2ubuntu1,
0.9.8.2-2ubuntu1.1)[/B][B]End-Date: 2014-10-01  10:03:06

*trimmed*[/B]

These are partial files that do not show he full boot process. In the last week or so, when I boot up, I get multiple lines of code showing some notes like** "Spawning upstart bridge too fast restarting"**
I can't get the lines to stop scrolling and I can't get print screen to copy. I've been using Ubuntu 14.04 since its stable release and I've never had this problem. The only thing I have changed in the past few years is to replace the CPU fan.
Everything else is the same.
Does anybody have a way to fix this? If I can get the scroll lock or the print screen to work I might get a better idea of the problems.
I hope this info is clear enough
Thanks

My system:
AMD Phenom 9850 quad core
ASUS Mobo M3A78 EM[COLOR=#888888]
[/COLOR]

---

### Post by deadflowr on 2015-08-09
That entry is exactly what an apt history entry should look like.
That said, is that from history.log.1.gz?
If so, it's pretty old.
Do you not have any regular file history.log?

Perhaps your system hasn't had any successful updates since the log rotated into the .gz archive.

I wonder what an apt-get update/apt-get upgrade will show?

---

### Post by vasa1 on 2015-08-09
> **Gnusboy said:**
> [IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]
I'm having a problem locating my current log files. When I go to a folder like **var log apt** I see many separate files starting with  "History.log.1.gz" and continuing through "History.log.12.gz" 
When I open them they show what appear to be boot files, but they are several months old and not current. Here is an example:
                        **Start-Date: 2014-10-01  10:02:53**[B]Commandline: aptdaemon
role='role-commit-packages' sender=':1.78'[/B][B]Upgrade: libvncserver0:amd64 (0.9.8.2-2ubuntu1,
0.9.8.2-2ubuntu1.1)[/B][B]End-Date: 2014-10-01  10:03:06

*trimmed*[/B]

These are partial files that do not show he full boot process. 
You should also see a file called **history.log**. That's the current one. The .gz ones are compressed by logrotate.

The purpose of files in */var/log/apt* is **not** to show the boot process.

Aargh! Ninja'ed yet again :(

---

### Post by Dennis N on 2015-08-09
Look at dmesg for startup events:

```
dmn@Roxanne:~$ cd /var/log
dmn@Roxanne:/var/log$ ls -l dmesg*
-rw-r----- 1 root adm 63105 Aug  8 20:29 dmesg
-rw-r----- 1 root adm 61378 Aug  6 14:54 dmesg.0
-rw-r----- 1 root adm 16983 Aug  3 21:44 dmesg.1.gz
-rw-r----- 1 root adm 16698 Aug  1 13:50 dmesg.2.gz
-rw-r----- 1 root adm 16582 Jul 31 15:06 dmesg.3.gz
-rw-r----- 1 root adm 16546 Jul 26 13:55 dmesg.4.gz

```
Notice that the older ones are archives.

A way to view log files is to install and use **gnome-system-log**

---

### Post by Gnusboy on 2015-08-09
OK. I found the current syslog and history logs. What is strange is that the most current log files are NOT labelled as just history.log
The most recent history files begin with different dates and are only partial files. Some start on Aug 02 and skip down to Aug. 07.2015.
Another file marked History log 08.09.20015 begins on July 07 2014 and ends on Aug. 1 2015. I've attached a couple of samples showing what I'm seeing. To me this is goofy as hell.
So, if y'all know how to fix this, I will appreciate any help you have to offer.
Thanks.

Syslog  08.09.2015

[ATTACH]263755[/ATTACH]

History log 08092015

[ATTACH]263756[/ATTACH]

History log 08.09.20015

[ATTACH]263757[/ATTACH]

---

