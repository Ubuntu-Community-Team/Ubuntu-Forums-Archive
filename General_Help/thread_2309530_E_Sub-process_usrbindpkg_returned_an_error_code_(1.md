---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-01-11
forum: General Help
---

### Post by Robin_strm on 2016-01-11
Had problems with mysql and tried to remove it, to install it again, but now every time I do sudo apt-get XXXX or sudo apt-get update it tires and tries and tries to fix the mysql install that got messed up. (My pc froze in the middle of the install, so had to manually shut it down to start it up again.)
What can i do to fix it? It's unable to fix for it self.  
(OS language is swedish and *m to lazy to translate everything by hand so used google translate, thats why it looks like it looks) 

```
robin @ HTPC: ~ $ sudo dpkg --configure -a
 [sudo] password for Robin:
 Sets the mysql-server-5.6 (5.6.27-0ubuntu1) ...
 Job for mysql.service failed Because a timeout was exceeded. See "systemctl status mysql.service" and "journalctl -xe" for details.
 invoke-rc.d: initscript mysql, action "start" failed.
 dpkg: error processing package mysql-server-5.6 (--configure): subprocess installed post-installation script returned error 1
 dpkg: dependency problems prevent configuration of mysql-server: mysql-server depends on mysql-server-5.6; however: Package mysql-server-5.6 is not configured yet.
 dpkg: error processing package mysql-server (--configure): dependency problems - leaving unconfigured
 Error encountered while processing: mysql-server-5.6 mysql-server

robin @ HTPC: ~ $ sudo apt-get install -f
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
0 upgrade, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, additional 0 B space used on the drive.
Sets the mysql-server-5.6 (5.6.27-0ubuntu1) ...
Job for mysql.service failed Because a timeout was exceeded. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.6 (--configure):
 during the process installed post-installation script returned error 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.6, but:
  Package mysql-server-5.6 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No kind report written because the error message indicates that there is a subsequent failure of the earlier problems.
                                           Error encountered while processing:
 mysql-server-5.6
 mysql-server
E: Sub-process / usr / bin / dpkg Returned an error code (1)



```

---

### Post by ian-weisser on 2016-01-11
Do you want to complete the install of mysql-server so you can use it?
Or do you want to remove mysql-server, and no longer wish to use it?

---

### Post by Robin_strm on 2016-01-11
Want to complete it for future use!

---

### Post by ian-weisser on 2016-01-11
> **Robin_strm said:**
> Job for mysql.service failed Because a timeout was exceeded. **See "systemctl status mysql.service" and "journalctl -xe" for details.**

Then those details would be helpful.

---

### Post by Robin_strm on 2016-01-11
Sure, but without sounding like a complete idiot, could you help me find them and specify what i need to post?

---

### Post by Robin_strm on 2016-01-12
Okay, sinse I'm to rookie on linux to yet figure out how to tell you those things, how do i delete mysql all together? Please help me! I'm going nut everytime I try to install something! Takes forever to do the simplest tasks! Please!

---

### Post by ian-weisser on 2016-01-12
Whoa.

Do you want to know how to uninstall MySql? Or do you want to finish installing it?
We cannot do both at once. Which do you want to do first?

Or do you want answers to some other question first?

That particular error is both uncommon and unusual. Most Ubuntu users never see it.
We will need to guide you through logs and other troubleshooting. It may be lengthy. Are you up for it?
Have you made any changes to your system since installing Ubuntu? Installed other software, changed settings?

---

### Post by Robin_strm on 2016-01-14
It seems to be easier to just remove/uninstall it at this point, I'm up for a challenge, but I don't think I have the skill set for it atm! 
I just want to get rid of that error message as quick as possible. So if uninstalling it goes faster, then I'll do that. 
Already tried "sudo apt-get remove mysql-server" but that doesn't work..
I've installed kodi, pipelight, conky, and some other small programs, but nothing huge!

---

### Post by ian-weisser on 2016-01-14
Okay, removing mysql-server.

Please show us the complete output of "sudo apt-get remove mysql-server"
Let's see what doesn't work.

---

### Post by Robin_strm on 2016-01-21
Sorry for the delay, I'm about to move to a new apartment so been kind of busy. Here's the output from "sudo apt-get remove mysql-server" :
```
robin @ HTPC: ~ $ sudo apt-get remove mysql-server
[sudo] password for robin:
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
The following packages will be REMOVED:
  mysql-server
0 upgrade, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 129 kB of additional disk space.
Do you want to continue? [Y / n] y
(Reading database ... 226441 files and directories currently installed.)
Remove mysql-server (5.6.27-0ubuntu1) ...
Setting up mysql-server-5.6 (5.6.27-0ubuntu1) ...
Job for mysql.service failed Because a timeout was exceeded. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.6 (--configure):
 during the process installed post-installation script returned error 1
Error encountered while processing:
 mysql-server-5.6
E: Sub-process / usr / bin / dpkg Returned an error code (1)
```


If some words aren't 100% right, it's because I translated in google translate from swedish. 
I Don't know where to find "systemctl status mysql service" and "journalctl -xe" with details, so if you need that, please help me find it!

---

### Post by Robin_strm on 2016-01-21
I googled around a bit and figured it out! Here's more details.

Systemctl status mysql.service : 
```
robin@HTPC:~$ systemctl status mysql.service -l
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: activating (start-post) since tor 2016-01-21 23:00:48 CET; 9min ago
  Process: 1507 ExecStart=/usr/bin/mysqld_safe (code=exited, status=0/SUCCESS)
  Process: 1504 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 1507 (code=exited, status=0/SUCCESS);         : 1508 (mysql-systemd-s)
   CGroup: /system.slice/mysql.service
           &#9492;&#9472;control
             &#9500;&#9472;1508 /bin/bash /usr/share/mysql/mysql-systemd-start post
             &#9492;&#9472;4535 sleep 1

jan 21 23:00:48 HTPC systemd[1]: Starting MySQL Community Server...
jan 21 23:00:48 HTPC mysqld_safe[1507]: error: Found option without preceding group in config file: /etc/mysql/my.cnf at line: 23
jan 21 23:00:48 HTPC mysqld_safe[1507]: Fatal error in defaults handling. Program aborted
jan 21 23:00:48 HTPC mysqld_safe[1507]: error: Found option without preceding group in config file: /etc/mysql/my.cnf at line: 23
jan 21 23:00:48 HTPC mysqld_safe[1507]: Fatal error in defaults handling. Program aborted
jan 21 23:00:48 HTPC mysqld_safe[1507]: 160121 23:00:48 mysqld_safe Logging to '/var/lib/mysql/HTPC.err'.
jan 21 23:00:48 HTPC mysqld_safe[1507]: 160121 23:00:48 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql


```

Journalctl -xe :
```
robin@HTPC:~$ journalctl -xe
-- The result is failed.
jan 21 23:10:48 HTPC systemd[1]: mysql.service: Unit entered failed state.
jan 21 23:10:48 HTPC systemd[1]: mysql.service: Failed with result 'timeout'.
jan 21 23:10:49 HTPC systemd[1]: mysql.service: Service hold-off time over, sche
jan 21 23:10:49 HTPC systemd[1]: Stopped MySQL Community Server.
-- Subject: Unit mysql.service has finished shutting down
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit mysql.service has finished shutting down.
jan 21 23:10:49 HTPC systemd[1]: Starting MySQL Community Server...
-- Subject: Unit mysql.service has begun start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit mysql.service has begun starting up.
jan 21 23:10:49 HTPC mysqld_safe[4786]: error: Found option without preceding gr
jan 21 23:10:49 HTPC mysqld_safe[4786]: Fatal error in defaults handling. Progra
jan 21 23:10:49 HTPC mysqld_safe[4786]: error: Found option without preceding gr
jan 21 23:10:49 HTPC mysqld_safe[4786]: Fatal error in defaults handling. Progra
jan 21 23:10:49 HTPC mysqld_safe[4786]: 160121 23:10:49 mysqld_safe Logging to '
jan 21 23:10:49 HTPC mysqld_safe[4786]: 160121 23:10:49 mysqld_safe Starting mys
jan 21 23:10:49 HTPC mysqld_safe[4786]: 160121 23:10:49 mysqld_safe mysqld from 
lines 1902-1924/1924 (END)


```

---

### Post by Robin_strm on 2016-01-21
So, i solved it myself! 
Edited out line 23 in my.cnf and that did the trick!

---

