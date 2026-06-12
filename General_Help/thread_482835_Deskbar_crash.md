---
title: "Deskbar crash"
date: 2007-06-24
forum: General Help
---

### Post by Cable on 2007-06-24
I've added Deskbar to my panel.  It crashes every time I log in.  Here is the text from the crash details dialog.
```

Distribution: Ubuntu 7.04 (feisty)
Gnome Release: 2.18.1 2007-04-10 (Ubuntu)
BugBuddy Version: 2.18.1

System: Linux 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
X Vendor: The X.Org Foundation
X Vendor Release: 70200000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Human
Icon Theme: Human

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0



----------- .xsession-errors (17 sec old) ---------------------
alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80d7360: Received at thread b3e41b90
alarm-queue.c:2008 (alarm_queue_add_async) - 0x80cfe80
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e5218: Replied to GUI thread
alarm-queue.c:560 (load_alarms_for_today) - From Sun Jun 24 03:56:25 2007
 to Sun Jun 24 03:56:25 2007
alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80d92a0: Received at thread b3e41b90
alarm-queue.c:2008 (alarm_queue_add_async) - 0x80d61b0
alarm-notify.c:337 (alarm_msgport_rep** Message: <information>    You are now connected to the wireless network 'Bankord'.
--------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/deskbar/ModuleLoader.py", line 157, in load_all
    self.load (f)
  File "/usr/lib/python2.5/site-packages/deskbar/ModuleLoader.py", line 139, in load
    mod_instance = getattr (mod, handler) ()
  File "/usr/lib/deskbar-applet/handlers/tracker-handler.py", line 201, in __init__
    self.tracker = bus.get_object('org.freedesktop.Tracker','/org/freedesktop/tracker')
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 410, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 230, in __init__
    _dbus_bindings.UInt32(0))
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```
What does it mean?  What can I do to fix this crash?  Deskbar is a very handy app!

---

### Post by Cable on 2007-06-27
*Bump*

I do have tracker and the tracker search plugin for deskbar installed.  I see the word "tracker" in there a couple of times.  Does it have something to do with that?

---

### Post by dirken on 2007-06-28
> **Cable said:**
> *Bump*

I do have tracker and the tracker search plugin for deskbar installed.  I see the word "tracker" in there a couple of times.  Does it have something to do with that?

Indeed this is all caused by the tracker app, just having the same issue and already reported it a few times: [http://bugzilla.gnome.org/show_bug.cgi](http://bugzilla.gnome.org/show_bug.cgi)
But still nothing!

---

### Post by stryderjzw on 2007-10-18
Hi,

What bug id is it?

I'm having Deskbar crashes as well and it's bugging me.  :)

Thanks,
Justin

---

