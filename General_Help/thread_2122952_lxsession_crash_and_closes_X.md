---
title: "lxsession crash and closes X"
date: 2013-03-06
forum: General Help
---

### Post by Israeru on 2013-03-06
Hello

I have a new installation of Lubuntus 12.10 32 bits for a PIM video server, the thing works well but yestarday and today at the same hour (between 11:50 am and 12:00 pm) the server crash, i mean the Xs are gone and the server goes to black screen. This server is located in a very remote area (a trip of 24 h to reach the installation) and i like to resolve this situation in remote form.

Now i share my findings:

I think that lxsession crash its the guilty, well the logs reports that lxsession die:

Mar  6 11:43:16 nodecamsrv kernel: [429098.986448] Core dump to |/usr/share/apport/apport 13511 6 4294967295 pipe failed
Mar  6 12:00:00 nodecamsrv kernel: [430102.924399] x-session-manag[11977]: segfault at 0 ip b6ce9457 sp bfe942bc error 4 in libc-2.15.so[b6bb8000+1a3000]

And in /var/crash i found something interesting:
ls -alh
total 324K
drwxrwsrwt  2 root whoopsie 4,0K mar  6 12:00 .
drwxr-xr-x 14 root root     4,0K mar  6 12:00 ..
-rw-rw----  1 root whoopsie    0 mar  6 12:00 .lock
-rw-r-----  1 root whoopsie 313K mar  6 12:00 _usr_bin_lxsession.0.crash

an extract from that file:
[SIZE=3][SIZE=2][SIZE=1]
ProblemType: Crash
Architecture: i386
Date: Wed Mar  6 12:00:00 2013
DistroRelease: Ubuntu 12.10
ExecutablePath: /usr/bin/lxsession
ExecutableTimestamp: 1347226237
ProcCmdline: x-session-manager
ProcCwd: /root
ProcEnviron:
 LANGUAGE=es_NI:es
 TERM=xterm
 PATH=(custom, no user)
 XDG_RUNTIME_DIR=<set>
 LANG=es_NI.UTF-8
 SHELL=/bin/bash
ProcMaps:
 08048000-08075000 r-xp 00000000 08:05 131338     /usr/bin/lxsession
 08075000-08076000 r--p 0002c000 08:05 131338     /usr/bin/lxsession
 08076000-08077000 rw-p 0002d000 08:05 131338     /usr/bin/lxsession
 08239000-0829f000 rw-p 00000000 00:00 0          [heap]
 b5800000-b5821000 rw-p 00000000 00:00 0
 b5821000-b5900000 ---p 00000000 00:00 0
 b59bb000-b59bc000 ---p 00000000 00:00 0
 b59bc000-b61bc000 rw-p 00000000 00:00 0          [stack:11982]
[/SIZE][/SIZE][/SIZE]

And in /var/log/syslog found something too:
Mar  6 11:43:16 nodecamsrv kernel: [429098.986448] Core dump to |/usr/share/apport/apport 13511 6 4294967295 pipe failed
Mar  6 12:00:00 nodecamsrv kernel: [430102.924399] x-session-manag[11977]: segfault at 0 ip b6ce9457 sp bfe942bc error 4 in libc-2.15.so[b6bb8000+1a3000]
Mar  6 12:00:33 nodecamsrv kernel: Kernel logging (proc) stopped.
Mar  6 12:00:33 nodecamsrv rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="881" x-info="http://www.rsyslog.com"] exiting on signal 15.
Mar  6 12:01:00 nodecamsrv kernel: imklog 5.8.6, log source = /proc/kmsg started.
Mar  6 12:01:00 nodecamsrv rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="505" x-info="http://www.rsyslog.com"] start
Mar  6 12:01:00 nodecamsrv rsyslogd: rsyslogd's groupid changed to 103
Mar  6 12:01:00 nodecamsrv rsyslogd: rsyslogd's userid changed to 101
Mar  6 12:01:00 nodecamsrv rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]


Now i think that the perpretator its identified.. but what i can do?

I install lubuntu and now this thing its failling, can i install xfce and change to xubuntu?

How i can install xfce in ubuntu?

I see a old bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1017244](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1017244)

Any other advice?

Greetings and thanks in advance for your help.

---

### Post by Israeru on 2013-03-11
Please Help

---

