---
title: "huge .xsession-error STILL"
date: 2013-01-13
forum: General Help
---

### Post by JigglyWiggly_ on 2013-01-13
So I just installed a clean install of ubuntu 12.04

I have enabled vnc via the remote settings in ubuntu.



It's installed on a SSD, so I don't want to kill my SSD in a few days.


I had this problem on another machine on ubuntu 10.04, and I thoughtit would have definitely been fixed in ubuntu 12.04.1 LTS



what can I do to fix this?


Like I thought this was fixed, and i don't understand how this can't be fixed.

This is a brand new install....

[http://ubuntuforums.org/showthread.php?t=1517991&page=4](http://ubuntuforums.org/showthread.php?t=1517991&page=4)


i've seen this thread, but i can never find a good solution, and I don't want a solution that will wear down my SSD.

---

### Post by JigglyWiggly_ on 2013-02-04
fixed
just make a folder called .xsession-errors it can't write to a folder
been using it for a few weeks

---

### Post by omeomi on 2013-02-04
Please mark you thread as solved (use Thread Tools) so it is clear to everyone that your problem is solved.

---

### Post by Cheesemill on 2013-02-04
If you actually post the errors that are filling up your .xsession-error file then we can give you some hints to fixing it, rather than just using an ugly hack to prevent the log file from being written to.

You should always try and fix the cause of a problem, not just work around the resulting errors.

---

### Post by JigglyWiggly_ on 2013-05-31
this is being spammed over and over and over, new install ubuntu 12.04.2

```
2/05/2013 07:56:27 PM rfbAuthPasswordChecked: password check failed22/05/2013 07:56:32 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 07:56:32 PM   other clients:
22/05/2013 07:56:32 PM      86.35.30.98
22/05/2013 07:56:32 PM      86.35.30.98
22/05/2013 07:56:32 PM      86.35.30.98
22/05/2013 07:56:32 PM      86.35.30.98
22/05/2013 07:56:32 PM      86.35.30.98
22/05/2013 07:56:32 PM      86.35.30.98
22/05/2013 07:56:32 PM      86.35.30.98
22/05/2013 07:56:32 PM      86.35.30.98
22/05/2013 07:56:32 PM      86.35.30.98
22/05/2013 07:56:33 PM Client Protocol Version 3.4
22/05/2013 07:56:33 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 07:56:39 PM rfbAuthPasswordChecked: password check failed
22/05/2013 07:56:44 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 07:56:44 PM   other clients:
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:44 PM      86.35.30.98
22/05/2013 07:56:45 PM Client Protocol Version 3.4
22/05/2013 07:56:45 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 07:56:51 PM rfbAuthPasswordChecked: password check failed
22/05/2013 07:56:56 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 07:56:56 PM   other clients:
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:56 PM      86.35.30.98
22/05/2013 07:56:57 PM Client Protocol Version 3.4
22/05/2013 07:56:57 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 07:57:03 PM rfbAuthPasswordChecked: password check failed
22/05/2013 07:57:08 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 07:57:08 PM   other clients:
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:08 PM      86.35.30.98
22/05/2013 07:57:10 PM Client Protocol Version 3.4
22/05/2013 07:57:10 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 07:57:16 PM rfbAuthPasswordChecked: password check failed
22/05/2013 07:57:21 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 07:57:21 PM   other clients:
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:21 PM      86.35.30.98
22/05/2013 07:57:22 PM Client Protocol Version 3.4
22/05/2013 07:57:22 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 07:57:28 PM rfbAuthPasswordChecked: password check failed
22/05/2013 07:57:42 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 07:57:42 PM   other clients:
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:42 PM      86.35.30.98
22/05/2013 07:57:43 PM Client Protocol Version 3.4
22/05/2013 07:57:43 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 07:57:49 PM rfbAuthPasswordChecked: password check failed
22/05/2013 09:44:29 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 09:44:29 PM   other clients:
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM      86.35.30.98
22/05/2013 09:44:29 PM Client Protocol Version 3.4
22/05/2013 09:44:29 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 09:44:35 PM rfbAuthPasswordChecked: password check failed
22/05/2013 09:44:40 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 09:44:40 PM   other clients:
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:40 PM      86.35.30.98
22/05/2013 09:44:41 PM Client Protocol Version 3.4
22/05/2013 09:44:41 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 09:44:47 PM rfbAuthPasswordChecked: password check failed
22/05/2013 09:44:52 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 09:44:52 PM   other clients:
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM      86.35.30.98
22/05/2013 09:44:52 PM Client Protocol Version 3.4
22/05/2013 09:44:52 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 09:44:59 PM rfbAuthPasswordChecked: password check failed
22/05/2013 09:45:04 PM [IPv4] Got connection from client 86.35.30.98
22/05/2013 09:45:04 PM   other clients:
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:04 PM      86.35.30.98
22/05/2013 09:45:05 PM Client Protocol Version 3.4
22/05/2013 09:45:05 PM Ignoring minor version mismatch


** (vino-server:2157): WARNING **: Deferring authentication of '86.35.30.98' for 5 seconds




** (vino-server:2157): WARNING **: VNC authentication failure from '86.35.30.98'


22/05/2013 09:45:11 PM rfbAuthPasswordChecked: password check failed
22/05/2013 09:45:19 PM [IPv4] Got connection from client 86.35.30.98

```

---

