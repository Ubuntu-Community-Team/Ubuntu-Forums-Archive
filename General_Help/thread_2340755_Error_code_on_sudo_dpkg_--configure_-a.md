---
title: "Error code on sudo dpkg --configure -a"
date: 2016-10-21
forum: General Help
---

### Post by astarmathsandphysics on 2016-10-21
Just updated to 16.04 and after an update I get these errors

```
astarmathsandphysics@server:~$ sudo dpkg --configure -a
Setting up dovecot-core (1:2.2.22-1ubuntu2.1) ...
Job for dovecot.service failed because the control process exited with error code. See "systemctl status dovecot.service" and "journalctl -xe" for details.
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dovecot-lmtpd:
 dovecot-lmtpd depends on dovecot-core (= 1:2.2.22-1ubuntu2.1); however:
  Package dovecot-core is not configured yet.

dpkg: error processing package dovecot-lmtpd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-mysql:
 dovecot-mysql depends on dovecot-core (= 1:2.2.22-1ubuntu2.1); however:
  Package dovecot-core is not configured yet.

dpkg: error processing package dovecot-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-core (= 1:2.2.22-1ubuntu2.1); however:
  Package dovecot-core is not configured yet.

dpkg: error processing package dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-imapd:
 dovecot-imapd depends on dovecot-core (= 1:2.2.22-1ubuntu2.1); however:
  Package dovecot-core is not configured yet.

dpkg: error processing package dovecot-imapd (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dovecot-core
 dovecot-lmtpd
 dovecot-mysql
 dovecot-pop3d
 dovecot-imapd
astarmathsandphysics@server:~$ 

```

Tried all the usual things. Several times. How can I fix this?

---

### Post by astarmathsandphysics on 2017-02-13
After going round in great big circles - and fixing a few other things - I am back at the same point getting the same error

---

### Post by Bashing-om on 2017-02-13
astarmathsandphysics; Humm ..

Installed version should be:
> 
sysop@x1604:~$ apt list dovecot-core
Listing... Done
dovecot-core/xenial-updates 1:2.2.22-1ubuntu2.2 amd64
N: There is 1 additional version. Please use the '-a' switch to see it
sysop@x1604:~$ 

so that begs the question of what is holding dovecot-XX at " 1:2.2.22-1ubuntu2.1 " ?

show the result of terminal command:
```

apt-cache policy dovecot-core

``` to start the process of finding out the why .

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by astarmathsandphysics on 2017-02-13
Here it is
```
dovecot-core:
  Installed: (none)
  Candidate: 1:2.2.22-1ubuntu2.2
  Version table:
     1:2.2.22-1ubuntu2.2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
     1:2.2.22-1ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
```

---

### Post by Bashing-om on 2017-02-14
astarmathsandphysics; Hummm ....

> 
Dovecot is a mail server whose major goals are security and extreme reliability.


To that end let's see what results when we install:
```

sudo apt install dovecot-core

```

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to keep the package manager satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by astarmathsandphysics on 2017-02-14
This is the output
```
astarmathsandphysics@server:~$ sudo apt install dovecot-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dovecot-core is already the newest version (1:2.2.22-1ubuntu2.2).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up dovecot-core (1:2.2.22-1ubuntu2.2) ...
Job for dovecot.service failed because the control process exited with error code. See "systemctl status dovecot.service" and "journalctl -xe" for details.
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 dovecot-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2017-02-14
astarmathsandphysics; Yuk !

Does not make a lot of sense:
> 
dovecot-core:
  Installed: (none)

bk

dovecot-core is already the newest version (1:2.2.22-1ubuntu2.2).

yet, now does it ?

So we follow the package manager's advise to get a hint:
> 
See "systemctl status dovecot.service" and "journalctl -xe" for details.

--------------------

We get any hints ; executing in terminal:
```

systemctl status dovecot.service
journalctl -xe

```


More here that I do not know
[INDENT][INDENT][INDENT]But, willing to learn otherwise
[/INDENT][/INDENT][/INDENT]

---

### Post by astarmathsandphysics on 2017-02-14
Here it all is

```
astarmathsandphysics@server:~$ systemctl status dovecot.service
&#9679; dovecot.service - Dovecot IMAP/POP3 email server
   Loaded: loaded (/lib/systemd/system/dovecot.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2017-02-14 19:58:21 GMT; 2h 17min ago
     Docs: man:dovecot(1)
           http://wiki2.dovecot.org/
  Process: 22400 ExecStart=/usr/sbin/dovecot (code=exited, status=89)

Feb 14 19:58:21 server systemd[1]: Starting Dovecot IMAP/POP3 email server...
Feb 14 19:58:21 server dovecot[22400]: Fatal: service(pop3) access(/usr/lib/dovecot/pop3) failed: No such file or directory
Feb 14 19:58:21 server systemd[1]: dovecot.service: Control process exited, code=exited status=89
Feb 14 19:58:21 server systemd[1]: Failed to start Dovecot IMAP/POP3 email server.
Feb 14 19:58:21 server systemd[1]: dovecot.service: Unit entered failed state.
Feb 14 19:58:21 server systemd[1]: dovecot.service: Failed with result 'exit-code'.
astarmathsandphysics@server:~$ journalctl -xe
Feb 14 22:16:02 server postfix/qmgr[2648]: 2D7A1182275F: removed
Feb 14 22:16:02 server postfix/smtp[29032]: warning: no MX host for astarmathsandphysics.com has a valid address record
Feb 14 22:16:02 server postfix/smtp[29032]: 379F7182068E: to=<admin@astarmathsandphysics.com>, orig_to=<astarmathsandphysics@server.astarmathsandphysics.com>,
Feb 14 22:16:02 server postfix/qmgr[2648]: 379F7182068E: removed
Feb 14 22:16:03 server firefox.desktop[5194]: console.error:
Feb 14 22:16:03 server firefox.desktop[5194]:   Could not write session state file
Feb 14 22:16:03 server firefox.desktop[5194]:   Message: Unix error 13 during operation open on file /home/astarmathsandphysics/.mozilla/firefox/ohu5qhkn.defa
Feb 14 22:16:03 server firefox.desktop[5194]:   
Feb 14 22:16:09 server postfix/local[27699]: CA1B318223ED: to=<theeducationchannel@server.astarmathsandphysics.com>, orig_to=<theeducationchannel>, relay=loca
Feb 14 22:16:09 server postfix/qmgr[2648]: CA1B318223ED: removed
Feb 14 22:16:12 server kernel: [UFW BLOCK] IN=eth0 OUT= MAC=00:19:b9:d9:a1:f7:f0:f2:49:8e:c5:82:08:00 SRC=108.162.229.105 DST=192.168.0.10 LEN=40 TOS=0x00 PRE
Feb 14 22:16:19 server firefox.desktop[5194]: console.error:
Feb 14 22:16:19 server firefox.desktop[5194]:   Could not write session state file
Feb 14 22:16:19 server firefox.desktop[5194]:   Message: Unix error 13 during operation open on file /home/astarmathsandphysics/.mozilla/firefox/ohu5qhkn.defa
Feb 14 22:16:19 server firefox.desktop[5194]:   
Feb 14 22:16:34 server firefox.desktop[5194]: console.error:
Feb 14 22:16:34 server firefox.desktop[5194]:   Could not write session state file
Feb 14 22:16:34 server firefox.desktop[5194]:   Message: Unix error 13 during operation open on file /home/astarmathsandphysics/.mozilla/firefox/ohu5qhkn.defa
Feb 14 22:16:34 server firefox.desktop[5194]:   
Feb 14 22:16:49 server firefox.desktop[5194]: console.error:
Feb 14 22:16:49 server firefox.desktop[5194]:   Could not write session state file
Feb 14 22:16:49 server firefox.desktop[5194]:   Message: Unix error 13 during operation open on file /home/astarmathsandphysics/.mozilla/firefox/ohu5qhkn.defa
Feb 14 22:16:49 server firefox.desktop[5194]:   
Feb 14 22:17:01 server CRON[29041]: pam_unix(cron:session): session opened for user theeducationchannel by (uid=0)
Feb 14 22:17:01 server CRON[29042]: pam_unix(cron:session): session opened for user theeducationchannel by (uid=0)
Feb 14 22:17:01 server CRON[29044]: (theeducationchannel) CMD (php -q /var/www/theeducationchannel/actions/verify_converted_videos.php)
Feb 14 22:17:01 server CRON[29043]: (theeducationchannel) CMD (php -q /var/www/theeducationchannel/actions/video_convert.php)
Feb 14 22:17:02 server postfix/pickup[28960]: 180BA18206D8: uid=1005 from=<theeducationchannel>
Feb 14 22:17:02 server CRON[29041]: pam_unix(cron:session): session closed for user theeducationchannel
Feb 14 22:17:02 server postfix/cleanup[28769]: 180BA18206D8: message-id=<20170214221702.180BA18206D8@server.astarmathsandphysics.com>
Feb 14 22:17:02 server CRON[29042]: pam_unix(cron:session): session closed for user theeducationchannel
Feb 14 22:17:02 server postfix/qmgr[2648]: 180BA18206D8: from=<theeducationchannel@server.astarmathsandphysics.com>, size=1431, nrcpt=1 (queue active)
Feb 14 22:17:02 server postfix/pickup[28960]: 267B718223ED: uid=1005 from=<theeducationchannel>
Feb 14 22:17:02 server postfix/cleanup[28769]: 267B718223ED: message-id=<20170214221702.267B718223ED@server.astarmathsandphysics.com>
Feb 14 22:17:02 server postfix/qmgr[2648]: 267B718223ED: from=<theeducationchannel@server.astarmathsandphysics.com>, size=1400, nrcpt=1 (queue active)
Feb 14 22:17:02 server postfix/local[29034]: 180BA18206D8: to=<theeducationchannel@server.astarmathsandphysics.com>, orig_to=<theeducationchannel>, relay=loca
Feb 14 22:17:02 server postfix/qmgr[2648]: 180BA18206D8: removed
Feb 14 22:17:02 server postfix/local[27699]: 267B718223ED: to=<theeducationchannel@server.astarmathsandphysics.com>, orig_to=<theeducationchannel>, relay=loca
Feb 14 22:17:02 server postfix/qmgr[2648]: 267B718223ED: removed
Feb 14 22:17:04 server firefox.desktop[5194]: console.error:
Feb 14 22:17:04 server firefox.desktop[5194]:   Could not write session state file
Feb 14 22:17:04 server firefox.desktop[5194]:   Message: Unix error 13 during operation open on file /home/astarmathsandphysics/.mozilla/firefox/ohu5qhkn.defa
Feb 14 22:17:04 server firefox.desktop[5194]:   
Feb 14 22:17:19 server firefox.desktop[5194]: console.error:
Feb 14 22:17:19 server firefox.desktop[5194]:   Could not write session state file
Feb 14 22:17:19 server firefox.desktop[5194]:   Message: Unix error 13 during operation open on file /home/astarmathsandphysics/.mozilla/firefox/ohu5qhkn.defa
Feb 14 22:17:19 server firefox.desktop[5194]:   
Feb 14 22:17:34 server firefox.desktop[5194]: console.error:
Feb 14 22:17:34 server firefox.desktop[5194]:   Could not write session state file
Feb 14 22:17:34 server firefox.desktop[5194]:   Message: Unix error 13 during operation open on file /home/astarmathsandphysics/.mozilla/firefox/ohu5qhkn.defa
Feb 14 22:17:34 server firefox.desktop[5194]:   
Feb 14 22:17:47 server kernel: [UFW BLOCK] IN=eth0 OUT= MAC=00:19:b9:d9:a1:f7:f0:f2:49:8e:c5:82:08:00 SRC=64.233.166.95 DST=192.168.0.10 LEN=40 TOS=0x00 PREC=
Feb 14 22:17:47 server kernel: [UFW BLOCK] IN=eth0 OUT= MAC=00:19:b9:d9:a1:f7:f0:f2:49:8e:c5:82:08:00 SRC=64.233.166.95 DST=192.168.0.10 LEN=40 TOS=0x00 PREC=
Feb 14 22:17:47 server kernel: [UFW BLOCK] IN=eth0 OUT= MAC=00:19:b9:d9:a1:f7:f0:f2:49:8e:c5:82:08:00 SRC=64.233.166.95 DST=192.168.0.10 LEN=40 TOS=0x00 PREC=
Feb 14 22:17:49 server firefox.desktop[5194]: console.error:
Feb 14 22:17:49 server firefox.desktop[5194]:   Could not write session state file
Feb 14 22:17:49 server firefox.desktop[5194]:   Message: Unix error 13 during operation open on file /home/astarmathsandphysics/.mozilla/firefox/ohu5qhkn.defa
Feb 14 22:17:49 server firefox.desktop[5194]:   
Feb 14 22:17:49 server kernel: [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:f0:f2:49:8e:c5:82:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 
lines 962-1020/1020 (END)


```

---

### Post by Bashing-om on 2017-02-15
astarmathsandphysics; Ummpphhh ..

I have thought about this and slept on it .. and I just do not have the the knowledge about a mail server to offer constructive advise. Perhaps others here can chime in ?

As to FireFox .. we can check the permissions ( error 13) :
```

ls -al /home/astarmathsandphysics/.mozilla/firefox/

``` see if "you" own the files in the subdirectories .

[INDENT]I just stuck
[INDENT][INDENT][INDENT]do not know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by astarmathsandphysics on 2017-02-16
I am using sudo ... so have root permissions. All oth installs go ok.

---

