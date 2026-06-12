---
title: "pidgin plugin"
date: 2008-07-10
forum: General Help
---

### Post by anemptygun on 2008-07-10
I download a pidgin plugin for banshee 1.0 from [here]("http://www.madsoft.org/2008/06/23/small-bashee-10-status-plugin-for-pidgin/") and followed what it said put I cant seem to get it to work? anyone else used this, or any suggestions?

---

### Post by roquefilipe on 2008-07-10
assuming that pidgin and banshee are installed and running, you just have to run the script.

```
python pidgin_banshee_status.py
```

or give it run permissions:

```
chmod +x pidgin_banshee_status.py
```

and run it:

```
./pidgin_banshee_status.py
```

and try it. Changing songs should change the status on pidgin. 


To not have the script hanging on the console append a "&". 

If it works, then procede to make it start with ubuntu, just as the author said.

---

### Post by maddog39 on 2008-08-14
Hey anemptygun,

I am the author of the plugin. If it still does not work, could you post your terminal output (if any) and make sure both pidgin and banshee are running or it will fail to connect to them (although for me they automatically start up but I've seen both scenarios before). By the way, your nick sounds REALLY familiar to me, I think I know you from somewhere (not to get off topic though).

- Alec Hussey

---

### Post by jakethecake on 2008-08-19
[SIZE="2"]I get this error dump with pidgin 2.4.3 and Banshee 1.2.1.

```
jake@quad:~$ ./pidgin_banshee_status.py 
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "./pidgin_banshee_status.py", line 33, in bansheeStateChanged
    for account in self.pidgin.PurpleAccountsGetAllActive():
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.28 was not provided by any .service files
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "./pidgin_banshee_status.py", line 33, in bansheeStateChanged
    for account in self.pidgin.PurpleAccountsGetAllActive():
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.28 was not provided by any .service files
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "./pidgin_banshee_status.py", line 33, in bansheeStateChanged
    for account in self.pidgin.PurpleAccountsGetAllActive():
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.28 was not provided by any .service files
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "./pidgin_banshee_status.py", line 33, in bansheeStateChanged
    for account in self.pidgin.PurpleAccountsGetAllActive():
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.28 was not provided by any .service files
Traceback (most recent call last):
  File "./pidgin_banshee_status.py", line 51, in <module>
    gobject.MainLoop().run()
KeyboardInterrupt
jake@quad:~$ 

```

```
  1 #!/usr/bin/env python
  2 #+---------------------------------------------+
  3 #| Pidgin Banshee Status
  4 #+---------------------------------------------+
  5 #| Written by Alec Hussey
  6 #| Copyright (C) 2008 MadSoft
  7 #| Website: [www.madsoft.org](www.madsoft.org)
  8 #| License: GNU General Public License v3
  9 #+---------------------------------------------+
 10 
 11 import dbus, gobject
 12 from dbus.mainloop.glib import DBusGMainLoop
 13 
 14 class BansheeStatusPlugin:
 15         def __init__(self):
 16                 bus = dbus.SessionBus()
 17                 bus.add_signal_receiver(self.bansheeStateChanged,
 18                                         dbus_interface="org.bansheeproject.Banshee.PlayerEngine",
 19                                         signal_name="StateChanged")
 20 
 21                 self.pidgin = bus.get_object("im.pidgin.purple.PurpleService", "/im/pidgin/purple/PurpleObject")
 22                 self.pidgin = dbus.Interface(self.pidgin, "im.pidgin.purple.PurpleInterface")
 23                 self.banshee = bus.get_object("org.bansheeproject.Banshee", "/org/bansheeproject/Banshee/PlayerEngin    e")
 24 
 25         def __resetPidginStatusMessage(self, message):
 26                 # Set new status message for the currently playing song
 27                 status = self.pidgin.PurpleSavedstatusGetCurrent()
 28                 self.pidgin.PurpleSavedstatusSetMessage(status, "Banshee: " + message)
 29                 self.pidgin.PurpleSavedstatusActivate(status)
 30 
 31         def bansheeStateChanged(self, state):
 32                 # Loop through all active accounts
 33                 for account in self.pidgin.PurpleAccountsGetAllActive():
 34                         # Get currently playing song from banshee
 35                         currentTrack = self.banshee.GetCurrentTrack()
 36 
 37                         # Reset pidgin status message with current track information
 38                         if state == "playing":
 39                                 self.__resetPidginStatusMessage(currentTrack['artist'] + " - " + currentTrack['name'    ])
 40                         elif state == "paused":
 41                                 self.__resetPidginStatusMessage("Paused")
 42 
 43 if __name__ == "__main__":
 44         # Setup dbus glib mainloop
 45         dbus.mainloop.glib.DBusGMainLoop(set_as_default=True)
 46 
 47         # Create new instance of our plugin class
 48         BansheeStatusPlugin()
 49 
 50         # Get main loop and run it
 51         gobject.MainLoop().run()

```

```
jake@quad:~$ dbus-monitor 
signal sender=org.freedesktop.DBus -> dest=:1.32 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.32"
method call sender=:1.32 -> dest=org.freedesktop.DBus path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=AddMatch
   string "type='method_call'"
method call sender=:1.32 -> dest=org.freedesktop.DBus path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=AddMatch
   string "type='method_return'"
method call sender=:1.32 -> dest=org.freedesktop.DBus path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=AddMatch
   string "type='error'"
method call sender=:1.30 -> dest=org.freedesktop.DBus path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameHasOwner
   string "org.gnome.Banshee"
method call sender=:1.30 -> dest=org.freedesktop.DBus path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameHasOwner
   string "org.gnome.Banshee"
signal sender=:1.30 -> dest=(null destination) path=/im/pidgin/purple/PurpleObject; interface=im.pidgin.purple.PurpleInterface; member=BuddyStatusChanged
   int32 6970
   int32 6962
   int32 6961
signal sender=:1.30 -> dest=(null destination) path=/im/pidgin/purple/PurpleObject; interface=im.pidgin.purple.PurpleInterface; member=BuddyStatusChanged
   int32 6503
   int32 6496
   int32 6494
method call sender=:1.30 -> dest=org.freedesktop.DBus path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameHasOwner
   string "org.gnome.Banshee"
signal sender=:1.30 -> dest=(null destination) path=/im/pidgin/purple/PurpleObject; interface=im.pidgin.purple.PurpleInterface; member=JabberSendingXmlnode
   int32 7694
   int32 31138
signal sender=:1.30 -> dest=(null destination) path=/im/pidgin/purple/PurpleObject; interface=im.pidgin.purple.PurpleInterface; member=JabberSendingText
   int32 7694
   string "<iq type='get' id='purple346d205d'><ping xmlns='urn:xmpp:ping'/></iq>"
signal sender=:1.30 -> dest=(null destination) path=/im/pidgin/purple/PurpleObject; interface=im.pidgin.purple.PurpleInterface; member=JabberReceivingXmlnode
   int32 7694
   int32 31142
method call sender=:1.30 -> dest=org.freedesktop.DBus path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameHasOwner
   string "org.gnome.Banshee"
method call sender=:1.30 -> dest=org.freedesktop.DBus path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameHasOwner
   string "org.gnome.Banshee"

```

[/SIZE]

---

### Post by ninboy on 2008-10-05
Sorry to open this thread again, but have anyone find a solution for this? I'm willing to use Pidgin/Banshee

---

### Post by anemptygun on 2009-03-01
So if I am understanding this correctly banshee **MUST**be open before running this script?

---

### Post by Tibuda on 2009-03-01
Have you tried [pidgin-musictracker package]("apt:pidgin-musictracker")? It works with XMMS, Audacious, Amarok, Rhythmbox, Banshee, QuodLibet, MPD and Exaile.

---

### Post by anemptygun on 2009-03-01
I have, but I cannot seem to get it to work. I put the parameters in the status message (%p | %a | %t) and make sure i have all of the setting enabled correctly in the plugin but nothing happens.

I am using banshee btw.

p.s. I have myself added as a contact on AIM so I can see my status change to make sure it's working.

---

### Post by theelk801 on 2009-03-14
I've installed the Music Tracker as well and I'm having the same problem. Could anyone shed some light on it?

---

