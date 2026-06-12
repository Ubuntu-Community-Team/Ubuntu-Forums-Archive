---
title: "WINE &amp; Steam.exe C++ Runtime Error"
date: 2006-10-28
forum: General Help
---

### Post by Centrino on 2006-10-28
Dear friends.

Note: Before I posted this, I researched and looked over past forum threads to seek solution (unable to find.)

I have WINE version 0.9.9, using Ubuntu Drapper 6.06 LTS 32-Bit. I successfully install SteamInstall.exe along with it's update, finally once it has completed the update, it proceeds to load Steam.exe.

Problem: It now throws the following error when loading Steam.exe, forcing Steam.exe to completely end task.

[IMG]http://img95.imageshack.us/img95/107/screenshotel7.png[/IMG]

Now, I really do not know how to resolve this issue. I have installed VB C++ 6.0 Runtime files, which installs accordingly. This only happens to Steam.exe and some other applications.

Following this error, in Terminal, it appears the following:

```
err:ntdll:RtlpWaitForCriticalSection section 0x7ffdcce4 "loader.c: loader_section" wait timed out in thread 000f, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7ffdcce4 "loader.c: loader_section" wait timed out in thread 0010, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7ffdcce4 "loader.c: loader_section" wait timed out in thread 0011, blocked by 0009, retrying (60 sec)
```

Is there any real solutions to this inferior problem?

---

### Post by Centrino on 2006-10-28
If it's at any help, in Steam.log reports a series of these errors, all the same:


CsComm        Session               Oct-28-2006  17:46:24.667  [15]  ReconnectThread (15) Starting





CsComm        Session               Oct-28-2006  17:51:10.342  [19]  ReconnectThread (19) Starting





CsComm        Session               Oct-28-2006  17:54:17.525  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  17:56:35.790  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  17:58:08.702  [16]  ReconnectThread (16) Starting





CsComm        Session               Oct-28-2006  18:02:51.002  [16]  ReconnectThread (16) Starting





CsComm        Session               Oct-28-2006  18:03:10.060  [28]  ReconnectThread (28) Starting





CsComm        Session               Oct-28-2006  18:03:24.571  [40]  ReconnectThread (40) Starting





CsComm        Session               Oct-28-2006  18:04:26.954  [16]  ReconnectThread (16) Starting





CsComm        Session               Oct-28-2006  18:06:16.831  [16]  ReconnectThread (16) Starting





CsComm        Session               Oct-28-2006  18:16:40.818  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  18:21:02.275  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  18:26:53.694  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  18:27:05.176  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  18:29:03.342  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  18:56:19.286  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  19:28:35.663  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  19:35:41.294  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  20:12:05.394  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  20:23:45.667  [22]  ReconnectThread (22) Starting





CsComm        Session               Oct-28-2006  20:24:07.902  [34]  ReconnectThread (34) Starting





CsComm        Session               Oct-28-2006  20:29:18.061  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  20:36:00.357  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  20:54:33.493  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  21:13:15.732  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  21:36:31.480  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  21:37:40.358  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  21:42:52.927  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  21:57:52.213  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  22:06:52.673  [14]  ReconnectThread (14) Starting





CsComm        Session               Oct-28-2006  22:07:31.547  [14]  ReconnectThread (14) Starting

---

