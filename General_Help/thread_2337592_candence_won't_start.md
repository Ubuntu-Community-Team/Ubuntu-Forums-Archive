---
title: "candence won't start"
date: 2016-09-19
forum: General Help
---

### Post by franklinrmaui on 2016-09-19
Thanks in advance having trouble getting cadence to start in KX-Studio 14.04.  The icon spins in the tray at the bottom then dissapears.  I want to run my version of pianoteq live with my Skullcanyon mini power house PC from INtel.
Franklin Russell
```
franklin@Franklinstienskullcanyon:~$ cadence-session-start --system-start


ERROR:dbus.proxies:Introspect error on :1.18:/org/jackaudio/Controller: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
tryCloseJackDBus() failed
Traceback (most recent call last):
  File "/usr/share/cadence/src/cadence_session_start.py", line 234, in <module>
    sys.exit(startSession(True, arg == "--system-start-desktop"))
  File "/usr/share/cadence/src/cadence_session_start.py", line 116, in startSession
    startJack()
  File "/usr/share/cadence/src/cadence_session_start.py", line 147, in startJack
    DBus.jack.StartServer()
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
franklin@Franklinstienskullcanyon:~$ 
franklin@Franklinstienskullcanyon:~$ cadence-session-start --system-start
ERROR:dbus.proxies:Introspect error on :1.85:/org/jackaudio/Controller: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
tryCloseJackDBus() failed
Traceback (most recent call last):
  File "/usr/share/cadence/src/cadence_session_start.py", line 234, in <module>
    sys.exit(startSession(True, arg == "--system-start-desktop"))
  File "/usr/share/cadence/src/cadence_session_start.py", line 116, in startSession
    startJack()
  File "/usr/share/cadence/src/cadence_session_start.py", line 147, in startJack
    DBus.jack.StartServer()
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)                                                                                                                                                                                                                                                          
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.                                                                                                                                                                                                                                                                         
franklin@Franklinstienskullcanyon:~$
```

---

