---
title: "help with /var/log files"
date: 2012-12-06
forum: General Help
---

### Post by Michele S on 2012-12-06
Hi there... my stupid brother deleted all the files recursively (but leaving the subdirectory) in /var/log with rm command...

Does these files get regenerated in automatic by rsyslog deamon ? If not there something i can do to force the respawn of these files? I noticed that a lot of log files respawned, but the file "lastlog" for example it didn't respawn, so i forced them with touch lastlog... there's a method to force the respawn of all log files? Or i simply shouldn't care about them cuz the importants log respawn in auto? 

Here's my /var/log content:

```
-rw-r--r-- 1 root              root        346 dic  6 21:31 alternatives.log
drwxr-xr-x 2 root              root       4096 dic  6 21:31 apt
-rw-r----- 1 syslog            adm       12126 dic  7 02:19 auth.log
-rw-r--r-- 1 root              root       1410 dic  7 01:51 boot.log
drwxr-xr-x 2 root              root       4096 dic  6 20:40 ConsoleKit
drwxr-xr-x 2 root              root       4096 dic  7 01:29 cups
drwxr-xr-x 2 root              root       4096 apr 20  2012 dist-upgrade
-rw-r--r-- 1 root              adm       55365 dic  7 01:51 dmesg
-rw-r--r-- 1 root              adm       55467 dic  7 01:08 dmesg.0
-rw-r--r-- 1 root              adm       14391 dic  6 20:41 dmesg.1.gz
-rw-r--r-- 1 root              root         28 dic  6 20:41 dmesg.2.gz
-rw-r--r-- 1 root              root      20877 dic  7 01:49 dpkg.log
-rw------- 1 root              root       2336 dic  7 01:51 fail2ban.log
drwxr-xr-x 2 root              root       4096 dic  6 20:31 fsck
drwxrwx--T 2 root              gdm        4096 dic  7 01:51 gdm
drwxr-xr-x 2 root              root       4096 apr  4  2012 hp
drwxr-xr-x 2 root              root       4096 dic  6 20:31 installer
-rw-r----- 1 syslog            adm      259746 dic  7 02:19 kern.log
-rw-r--r-- 1 root              root     292292 dic  7 02:18 lastlog
-rw-r----- 1 syslog            adm           0 dic  6 20:41 mail.err
-rw-r----- 1 syslog            adm           0 dic  6 20:41 mail.log
-rw-r----- 1 syslog            adm      205697 dic  7 02:19 messages
drwxr-s--- 2 mysql             adm        4096 nov 12 21:08 mysql
drwxr-xr-x 2 root              root       4096 dic  6 20:41 news
-rw-r--r-- 1 root              root      11499 dic  7 01:51 pm-powersave.log
drwx------ 2 speech-dispatcher root       4096 feb  6  2012 speech-dispatcher
drwxr-xr-x 2 stunnel4          stunnel4   4096 dic  6 20:31 stunnel4
-rw-r----- 1 syslog            adm      140796 dic  7 02:19 syslog
-rw-r----- 1 syslog            adm      220527 dic  7 01:27 syslog.1
-rw-r--r-- 1 root              root     263709 dic  7 01:51 udev
-rw-r----- 1 syslog            adm        1558 dic  7 01:53 ufw.log
-rw-r----- 1 syslog            adm        1462 dic  7 01:15 ufw.log.1
drwxr-xr-x 2 root              root       4096 mar 12  2012 unattended-upgrades
drwxr-xr-x 2 root              root       4096 dic  7 01:52 upstart
-rw-r--r-- 1 root              root      58738 dic  7 02:19 Xorg.0.log
-rw-r--r-- 1 root              root      56337 dic  7 01:51 Xorg.0.log.old
```

---

### Post by SeijiSensei on 2012-12-06
They will all get rebuilt eventually.

Perhaps you should reconsider who should have root privileges on your machine.

---

### Post by Michele S on 2012-12-06
> **SeijiSensei said:**
> They will all get rebuilt eventually.

Perhaps you should reconsider who should have root privileges on your machine.

Nice to hear... the first thing i'll do tomorrow is to remove his account from sudoers, thanks for the reply!

---

